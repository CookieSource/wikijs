---
title: Perform system snapshots and rollbacks with Timeshift on Btrfs
description: 
published: true
date: 2022-10-20T10:15:59.362Z
tags: 
editor: markdown
dateCreated: 2022-10-20T10:15:59.362Z
---

# Introduction
The snapshot feature of the Btrfs filesystem can be used to perform system snapshots and rollbacks, Timeshift is a user-friendly graphical application for that.
Unfortunately, the current Cnchi-based RebornOS installer only allows installation on the bare Btrfs filesystem, and not on the @ subvolume, which would be needed to perform system snapshots and rollbacks with Timeshift.

In this guide I will explain how to move your RebornOS installation to a Timeshift-compatible Btrfs subvolume layout. 

# Before you start
I would advise against using a boot partition (mount point `/boot`) with Btrfs system subvolumes, as that would exclude the /boot directory from system snapshots. A quick way to remove your boot partition is explained [here](remove-the-boot-partition) to remove your systems boot partition.

Check if your system partition uses Btrfs (`df -Th /`). If not, you can use Btrfs-convert to convert your system partition to Btrfs if it uses the ext2/3/4 or ReiserFS filesystem. The process is explained [here](convert-ext2-ext3-ext4-or-reiserfs-to-btrfs).

# Move RebornOS to Btrfs subvolumes
If you think you messed up a command in any of the following steps in this chapter, just run `sudo btrfs subvolume delete /@`, `sudo btrfs subvolume delete /@home` and `sudo btrfs subvolume delete /@temp` to revert your changes and contine at the beginning of this chapter with step 1.

1. First, create a snapshot of your system partition to /@:
`sudo btrfs subvolume snapshot / /@`
A snapshot is a normal subvolume, but it won't consume extra space as long as the content stays the same, because it can share all data blocks with the source subvolume. All files on your system partition are now present a second time on that subvolume.

2. Unless you want to use a separate home partition, run
`sudo btrfs subvolume create /@home && sudo find /@/home -mindepth 1 -prune -exec mv -v '{}' /@home`
to create a Timeshift-compatible home subvolume which lets you exclude the home directory /home from Btrfs system snapshots.

3. I also recommend creating additional subvolumes for all directories that should be excluded from Btrfs system snapshots and thereby preserved during system rollbacks.
For the following commands to work you'll first need to create a snapshot of the future system subvolume @: sudo btrfs subvolume snapshot /@ /@temp

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