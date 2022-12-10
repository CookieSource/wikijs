---
title: How to perform Boot Repair
description: Instructions for recovering a system that is unable to boot
published: true
date: 2022-12-10T19:49:35.499Z
tags: grub, bootloader, repair, recovery, boot recovery, boot repair, boot
editor: markdown
dateCreated: 2022-12-10T19:23:10.785Z
---

# Boot Repair for GRUB

If you are unable to boot into RebornOS, this guide will show you how to repair your bootloader using a live ISO.

## 1. Check if you are booted in *UEFI* or *Legacy* mode
If you are booted in *UEFI* mode, when you run the command `ls -ld /sys/firmware/efi`, you will see an output like
```sh
$ ls -ld /sys/firmware/efi
drwxr-xr-x 5 root root 0 Dec 10 09:52 /sys/firmware/efi/
```
If you are booted in *Legacy* mode, when you run the command `ls -ld /sys/firmware/efi`, you will see an output like
```sh
$ ls -ld /sys/firmware/efi
ls: cannot access /sys/firmware/efi: No such file or directory
```

## 2. Chroot into your installed RebornOS
Follow the instructions on [this page](chroot) to *chroot* into your locally installed RebornOS. 
> After *chroot*ing, please keep the same terminal window open to perform the below steps.

## 3. Re-Install GRUB
Based on whether you are booted in UEFI or Legacy mode, you can run the below
### UEFI mode
```sh
sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=RebornOS --recheck
```
### Legacy mode
```sh
sudo grub-install --target=i386-pc --bootloader-id=RebornOS --recheck
```
## 4. Recreate GRUB Configuration
```sh
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

## 5. Assess Reboot Safety
If the above `grub-install` and `grub-mkconfig` steps run successfully, it is safe to reboot!