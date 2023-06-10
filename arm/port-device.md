---
title: How to port RebornOS ARM to an unsupported device.
description: 
published: true
date: 2023-06-10T09:30:17.051Z
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


Try looking for a kernel that works with your device (in the aur or somewhere else)

If you have a device that can run RebornOS ARM already you can do something like this.
```
sudo pacman -Fy rk3588s-orangepi-5.dtb
```
## Modify a current image to make it work with your device
You can use this image and modify it to your needs
https://github.com/RebornOS-Developers/lxqt-rock5b-image

### Files you need to modify

> If your device is 32bit `armv7h` the packages and pacman.conf file become `packages.armv7h` and `pacman.conf.armv7h`
{.is-warning}

> There is no 32bit `armv7h` repo of RebornOS so you need to comment the RebornOS repo with `#`
{.is-warning}

> Changing the device in `profiledef` should only be done if you know what you are doing. <br> It is recommended to use `rock5b` and just replace `idbloader.img` and `u-boot.itb`
{.is-warning}




- profiledef (change arch, configtxt, cmdline, and img_name) 

- packages.aarch64 (you need to add the kernel pkg name to the list)
- pacman.conf.aarch64 (you need to make a local repo that contains the kernel pkg)

#### Making a local repo
  1. Make a new directory in the image dir (replace device with a short name for your device)
     ```sh
	   mkdir ~/lxqt-device-image/localrepo/
     cd ~/lxqt-device-image/localrepo/
     ```
  2. Get the packages you need
  3. Add them to a database
  	 ```
     repo-add localrepo.db.tar.gz pkgfile.pkg.tar.zst
     ```
  4. Edit pacman.conf.aarch64
     ```
     nano ~/lxqt-device-image/pacman.conf.aarch64
     ```
     Add this to it and replace USERNAME with your username 
     ```
     [localrepo]
     SigLevel = Never
     Server = file://home/USERNAME/lxqt-device-image/localrepo/
     ```