---
title: How to perform Boot Repair
description: Recover a system unable to boot
published: true
date: 2023-03-16T10:50:24.150Z
tags: bootloader, repair, grub, recovery, boot recovery, boot repair, boot
editor: markdown
dateCreated: 2023-02-18T16:54:50.621Z
---

# Boot Repair for GRUB
If you are unable to boot into RebornOS, this guide will show you how to repair your bootloader using a live ISO.

## 1. Check if you are booted in UEFI or Legacy mode
If you are booted in UEFI mode, when you run the command `ls -ld /sys/firmware/efi`, you will see an output like:
```
$ ls -ld /sys/firmware/efi
drwxr-xr-x 5 root root 0 Dec 10 09:52 /sys/firmware/efi/
```
If you are booted in Legacy mode, when you run the command above, you will see an output like:

```
$ ls -ld /sys/firmware/efi
ls: cannot access /sys/firmware/efi: No such file or directory
```

## Chroot into your installed RebornOS
Follow the instructions on this page to **chroot** into your locally installed RebornOS.

After chrooting, please keep the same terminal window open to perform the below steps.

## Re-install GRUB
Based on whether you are booted in UEFI or Legacy mode, you can run the below commands:

**UEFI mode**
``` 
sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=RebornOS --recheck
```
**Legacy mode**
```
sudo grub-install --target=i386-pc --bootloader-id=RebornOS --recheck 
```
## 4 Recreate GRUB configuration
```
sudo grub-mkconfig -o /boot/grub/grub.cfg 
```
## 5. Assess reboot safety
If the above `grub-install` and `grub-mkconfig` steps run successfully, it is safe to reboot!



