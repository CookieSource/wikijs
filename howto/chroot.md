---
title: How to chroot into your RebornOS
description: 
published: true
date: 2023-03-16T11:05:38.028Z
tags: chroot, chrooting
editor: markdown
dateCreated: 2023-02-18T16:55:11.414Z
---

# Chroot

## What is Chroot
Chroot is a way to change the root directory of a running Linux system. This means that you can access and manipulate files on a Linux installation as if you were logged into that system, even if you are actually running a different operating system.

## How to Chroot

1. Start your computer from a live Linux USB or DVD. This will allow you to access and modify the RebornOS installation.
2. Open a terminal window. A terminal is a text-based interface where you can type commands.
3. In the terminal, type the following command and press Enter:
This will create a new directory called "rebornos" in the "/mnt" directory.
```
mkdir /mnt/rebornos
```
4. Find the partition RebornOS is installed on
Type the following command to get a list of partitions.
``` 
lsblk
```
Find the partition your system is installed on generally this is the largest partition on SDA
in this example that would be sda2 as we want to mount the / partition 
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk 
├─sda1   8:1    0   512M  0 part /boot/efi
├─sda2   8:2    0   128G  0 part /
├─sda3   8:3    0 256.6G  0 part /home
└─sda4   8:4    0 546.2G  0 part /mnt/data
```

Where sdaX is the result you find in LSBLK in the above example that was sda2
```
mount /dev/sdaX /mnt/rebornos
```
5. Chroot into RebornOS
Type the following command
```
chroot /mnt/rebornos /bin/bash
```
Now if everything went well you're  in your RebornOS installation from here you can troubleshoot the issues on your system or revert breaking changes.