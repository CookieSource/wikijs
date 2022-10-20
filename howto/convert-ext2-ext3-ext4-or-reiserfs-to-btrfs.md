---
title: Convert ext2, ext3, ext4 or ReiserFS to Btrfs
description: 
published: true
date: 2022-10-20T09:51:02.632Z
tags: file system
editor: markdown
dateCreated: 2022-10-20T08:50:38.119Z
---

In case the partition you want to convert is your system partition you will need to perform the steps in this guide from another (GNU/Linux) operating system instance, like the RebornOS live ISO.

Do not perform this operation on data you can't afford to lose. There are reports of btrfs-convert failing, leaving behind a damaged partition.

1. Find out the device name of the partition you want to convert to Btrfs. `lsblk`, `fdisk -l` or a graphical partition manager are good ways to find the device name of the partition you want to convert.

2. If the partition is mounted, unmount it: sudo umount `/dev/<device name of partition>`

3. Run sudo `fsck -fy /dev/<device name of partition>` to check the file system for inconsistencies and repair them if possible. If issues were found, run again.

4. Run `sudo btrfs-convert --uuid copy /dev/<device name of partition>` to convert the file system to Btrfs. If no errors occurred, the file system should be Btrfs now.

In case the converted partition is a system partition:
To still be able to boot into the new Btrfs partition you have to perform the following steps:
1. Mount the system partition (`sudo mount /dev/<device name of partition> /mnt`), and into it also the matching EFI system partition (`sudo mount /dev/<device name of ESP > /mnt/boot/efi`).
2. Chroot into the system with `sudo arch-chroot /mnt`, then adjust the system's fstab (`nano /etc/fstab`) by adjusting the filesystem type to "btrfs" and removing/replacing eventual Btrfs-incompatible mount options.
3. Run `mkinitcpio -P` and `grub-mkconfig -o /boot/grub/grub.cfg`. You can now exit the chroot jail and reboot into your operating system, now on a Btrfs filesystem.

To take full advantage of the Btrfs filesystem features read the following guide: https://osdn.net/projects/rebornos/wiki/Btrfs%20system%20snapshots%20and%20rollbacks%20with%20Timeshift