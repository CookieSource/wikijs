---
title: How to port RebornOS ARM to an unsupported device.
description: 
published: true
date: 2023-03-11T17:51:30.610Z
tags: arm
editor: markdown
dateCreated: 2023-03-11T17:22:05.400Z
---

# How to port RebornOS ARM to an unsupported device.
# PAGE IS NOT FINISHED
## Research

Boot up Debian/Ubuntu on the device you want to port
Check what dtb it uses by looking at the extlinux.conf file
```
cat /boot/extlinux/extlinux.conf
```
look at the FDT line it should look like this

> fdt /dtbs/rockchip/rk3588s-orangepi-5.dtb
{.is-info}


Try looking for a kernel that works with your device

If you have a device that can run RebornOS already you can do something like this.
```
sudo pacman -Fy rk3588s-orangepi-5.dtb
```
