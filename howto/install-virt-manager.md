---
title: Install Virtual Machine Manager (virt-manager)
description: 
published: true
date: 2023-02-18T17:05:36.937Z
tags: 
editor: markdown
dateCreated: 2023-02-18T16:56:03.858Z
---

If you are using GNOME and have GNOME Boxes installed, you have the necessary Virt-manager dependencies.

GNOME Boxes installs with:
```
sudo pacman -S gnome-boxes ebtables bridge-utils netcat radvd dmidecode ceph qemu-block-gluster qemu-arch-extra qemu-block-iscsi qemu-block-rbd qemu-block-gluster
```
Virt-manager installs with:
```
sudo pacman -S virt-manager edk2-ovmf
```
The `edk2-ovmf` package provides UEFI support.

Activation of virt-manager is done with:
```
sudo systemctl enable --now libvirtd.service
```
Virt-manager dependencies are installed with (remember that if we have GNOME and we also have Gnome Boxes installed, this step is not needed):
```
sudo pacman -S qemu radvd dmidecode ceph qemu-block-gluster netcat bridge-utils ebtables
```
Then, your user must belong to the following groups:
```
libvirt
kvm
```
How do I add my user to these groups? Being \<user\> the name of my user, we can do it from the terminal with:
```
sudo gpasswd -a <usuario> libvirt
sudo gpasswd -a <usuario> kvm
```
Reboot the system and it is ready to use. 