---
title: How ro remove the boot partition
description: 
published: true
date: 2022-10-20T10:03:53.139Z
tags: 
editor: markdown
dateCreated: 2022-10-20T10:00:48.996Z
---

If your system currently uses a boot partition, but you want your `/boot` path to remain on your root partition instead of being separated out to a discrete partition, follow this guide.

> This guide assumes you are using the GRUB bootloader. Do not follow this guide if you installed RebornOS with systemd-boot as the bootloader, as it only supports FAT16/32 file systems and therefore needs an FAT16/32 boot partition in order to access the `/boot` directory.
{.is-warning}

1. Run `lsblk` and note the device name (first column) of the partition with mountpoint `/boot`.

2. Unmount the boot partition with `sudo umount /boot`

3. Mount it to another place with `sudo mount /dev/<device name of boot partition> /mnt`

4. Move all the content of the boot partition to the now empty /boot directory with `sudo mv -v /mnt/* /boot`.

5. Remove the line in `/etc/fstab` regarding the `/boot` partition. You can use nano to edit the file: `sudo nano /etc/fstab`

6. - If you are on an UEFI installation run `sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi`.

   - If you are on a legacy BIOS installation, run `sudo grub-install --target=i386-pc /dev/<device name of system disk>`.

8. After that run `sudo grub-mkconfig -o /boot/grub/grub.cfg`

You can now unmount the former boot partition with `sudo umount /mnt` and remove it in your partition manager of choice.