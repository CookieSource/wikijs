---
title: Perform system snapshots and rollbacks with Timeshift on Btrfs
description: 
published: true
date: 2023-02-18T17:05:59.342Z
tags: 
editor: markdown
dateCreated: 2023-02-18T16:56:41.546Z
---

# Introduction
The snapshot feature of the Btrfs filesystem can be used to perform system snapshots and rollbacks, Timeshift is a user-friendly graphical application for that.
Unfortunately, the current Cnchi-based RebornOS installer only allows installation on the bare Btrfs filesystem, and not on the @ subvolume, which would be needed to perform system snapshots and rollbacks with Timeshift.

In this guide I will explain how to move your RebornOS installation to a Timeshift-compatible Btrfs subvolume layout. 

# Before you start
I would advise against using a boot partition (mount point `/boot`) with Btrfs system subvolumes, as that would exclude the /boot directory from system snapshots. A quick way to remove your boot partition is explained [here](/howto/remove-the-boot-partition) to remove your systems boot partition.

Check if your system partition uses Btrfs (`df -Th /`). If not, you can use Btrfs-convert to convert your system partition to Btrfs if it uses the ext2/3/4 or ReiserFS filesystem. The process is explained [here](/howto/convert-ext2-ext3-ext4-or-reiserfs-to-btrfs).

# Move RebornOS to Btrfs subvolumes
If you think you messed up a command in any of the following steps in this chapter, just run `sudo btrfs subvolume delete /@`, `sudo btrfs subvolume delete /@home` and `sudo btrfs subvolume delete /@temp` to revert your changes and contine at the beginning of this chapter with step 1.

1. First, create a snapshot of your system partition to /@:
`sudo btrfs subvolume snapshot / /@`
A snapshot is a normal subvolume, but it won't consume extra space as long as the content stays the same, because it can share all data blocks with the source subvolume. All files on your system partition are now present a second time on that subvolume.

2. Unless you want to use a separate home partition, run
`sudo btrfs subvolume create /@home && sudo find /@/home -mindepth 1 -prune -exec mv -v '{}' /@home`
to create a Timeshift-compatible home subvolume which lets you exclude the home directory /home from Btrfs system snapshots.

3. I also recommend creating additional subvolumes for all directories that should be excluded from Btrfs system snapshots and thereby preserved during system rollbacks.
For the following commands to work you'll first need to create a snapshot of the future system subvolume @:
`sudo btrfs subvolume snapshot /@ /@temp`

You can now execute the following commands to replace the relevant directories in the @ subvolume with Btrfs subvolumes of the same name and move the content snapshotted to subvolume @temp back to its place:
`/var/cache` and `/var/tmp` contain only temporary files, which are either not essential or can be recomputed or redownloaded anytime. Exclude them to keep snapshots small:
`sudo rm -rfv /@/var/cache && sudo btrfs subvolume create /@/var/cache && sudo find /@temp/var/cache -mindepth 1 -prune -exec mv -v '{}' /@/var/cache`
`sudo rm -rfv /@/var/tmp && sudo btrfs subvolume create /@/var/tmp && sudo find /@temp/var/tmp -mindepth 1 -prune -exec mv -v '{}' /@/var/tmp`
`/var/log` contains system logs, which should be excluded from rollbacks so system issues can be diagnosed when booting into a snapshot:
`sudo rm -rfv /@/var/log && sudo btrfs subvolume create /@/var/log && sudo find /@temp/var/log -mindepth 1 -prune -exec mv -v '{}' /@/var/log`
/tmp is only used for temporary files and should therefore be excluded from system snapshots:
`sudo rm -rfv /@/tmp && sudo btrfs subvolume create /@/tmp`
Feel free to add more if you're feeling confident and think you know what you're doing, you might want to exclude databases, virtual machines and hosted websites for example, that are not stored under /home, to prevent them from rolling back with the system.

You can now safely remove the temporary @temp subvolume:
sudo btrfs subvolume delete /@temp

4. Make sure the top-level subvolume (id=5) is the default, otherwise Timeshift won't be able to create Btrfs system snapshots:
`sudo btrfs subvolume set-default 5 / `

# Edit the new system's file system table
To account for the changes, you have to edit /etc/fstab for the new RebornOS system on the new system subvolume, current path /@/etc/fstab.
You can use nano for that:
`sudo nano /@/etc/fstab`

Every subvolume that should be mounted during boot needs its own entry in fstab, a minimum entry for a non-default subvolume would look like this:
```
UUID=<UUID of filesystem the subvolume resides in>  btrfs  subvol=<path of subvolume relative to the top-level subvolume>  0 0
```
This is an example of how fstab could look like after editing:
```
UUID=11111111-1111-1111-1111-111111111111 /                     btrfs subvol=@,defaults,noatime,compress=zstd,discard=async 0 0
UUID=11111111-1111-1111-1111-111111111111 /home                 btrfs subvol=@home,defaults,compress=zstd                   0 0
UUID=11111111-1111-1111-1111-111111111111 /var/cache            btrfs subvol=@/var/cache                                    0 0
UUID=11111111-1111-1111-1111-111111111111 /var/tmp              btrfs subvol=@/var/tmp                                      0 0
UUID=11111111-1111-1111-1111-111111111111 /var/log              btrfs subvol=@/var/log                                      0 0
tmpfs                                     /tmp                  tmpfs defaults,mode=1777                                    0 0
UUID=0000-0000                            /boot/efi             vfat  defaults                                              0 2
UUID=22222222-2222-2222-2222-222222222222 swap                  swap  defaults                                              0 0
```
Btrfs mount options propagate down through mount points when the mounted subvolumes are on the same filesystem, unless a contradictory mount option that can be applied per-subvolume is specified for the sub-subvolume. That's why mount options defaults and compress are only specified once for the system subvolume.

# Mount your new RebornOS system to a temporary mountpoint
After editing `/@/etc/fstab`, the only thing left to do to make the new RebornOS system on the new system subvolume bootable is to reinstall the bootloader for the new RebornOS system, so it will actually boot the new system. To do this, you have to mount the new RebornOS system so you can chroot into it.

1. Find out the device name of the system partition (mount point /) and, if present, the EFI system partition (mount point /boot/efi). `lsblk`, `fdisk -l` or a graphical partition manager are good ways to do that.

2. Mount the new system subvolume to /mnt:
`sudo mount -o subvol=@ /dev/<device name of system partition> /mnt`
Mounting the @home subvolume (`sudo mount -o subvol=@home /dev/<device name of system partition> /mnt/home`) is not necessary. Now the only thing missing is the EFI system partition (if you have one):
/boot/efi:
`sudo mount /dev/<device name of EFI system partition> /mnt/boot/efi`
Now all necessary parts of your new RebornOS system should be mounted. 

# Chroot into the new system and reinstall GRUB
1. Chroot into the new RebornOS system:
`sudo arch-chroot /mnt`

2. Install the GRUB bootloader:
`grub-install`

3. After (re)installing the bootloader you also have to update the GRUB configuration file:
`grub-mkconfig -o /boot/grub/grub.cfg`

4. Run exit to leave the chroot jail. You can now reboot and should end up in the new RebornOS system on the @ subvolume. The system is now ready for Btrfs snapshots with Timeshift.

You might have to manually activate *cronie.service* by running `sudo systemctl enable --now cronie.service` for Timeshift scheduled snapshots to work.

# Remove the old RebornOS system
1. Mount the system subvolume to /mnt:
`sudo mount /dev/<device name of system partition> /mnt`

2. Remove everything except system subvolumes and their content from the system partition:
`sudo find /mnt -mindepth 1 -prune \! -name '@*' \! -name timeshift-btrfs -exec rm -rfv '{}' +`

# Boot into Timeshift snapshots from GRUB with grub-btrfs
When properly configured grub-btrfs allows you to easily boot into Timeshift Btrfs system snapshots and perform system rollbacks from there.

After installing grub-btrfs (`sudo pacman -S grub-btrfs`), GRUB boot entries for existing Timeshift Btrfs snapshots get created every time the GRUB configuration file gets updated (`sudo grub-mkconfig -o /boot/grub/grub.cfg`).

Grub-btrfs can perform the GRUB update automatically each time a new Timeshift Btrfs snapshot is created.

1. Run `sudo systemctl edit --full grub-btrfs.path` and replace the content with the following block of text:
```ini
 [Unit]
 Description=Monitors for new snapshots
 DefaultDependencies=no
 Requires=run-timeshift-backup.mount
 After=run-timeshift-backup.mount
 BindsTo=run-timeshift-backup.mount

 [Path]
 PathModified=/run/timeshift/backup/timeshift-btrfs/snapshots

 [Install]
 WantedBy=run-timeshift-backup.mount
```
This step is revertible with `systemctl revert grub-btrfs.path`.

2. Now you can activate the automatic update of the GRUB configuration file with
`sudo systemctl enable --now grub-btrfs.path`

Grub-btrfs can be further configured by editing `/etc/default/grub-btrfs/config`.

# Automatic system snapshot before package upgrades with timeshift-autosnap
You might also want to install timeshift-autosnap, which creates Timeshift snapshots before package upgrades using a pacman hook.
To prevent the Grub update from being performed twice when timeshift-autsnap creates a snapshot, I recommend changing the line `updateGrub=true` in `/etc/timeshift-autosnap.conf` to `updateGrub=false`.

I hope this guide helped you to successfully set up Btrfs system snapshots with Timeshift.
<hr>
-damian101