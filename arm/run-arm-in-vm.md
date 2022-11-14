---
title: How to run RebornOS arm in a VM on an x64-bit pc
description: Short article on how to run RebornOS ARM on an x86_64 pc using QEMU 
published: true
date: 2022-11-14T15:15:37.027Z
tags: 
editor: markdown
dateCreated: 2022-11-14T15:15:37.027Z
---

basic introduction

# Download image
https://github.com/RebornOS-Developers/qemu-images/releases/latest
download RebornOS-ARM-generic-2022-11-13.qcow2
# Install required deps
```sh
sudo pacman -S qemu virt-viewer libvirt virt-manager qemu-desktop edk2-armvirt
```
# Enable libvirtd service
```sh
sudo systemctl enable --now libvirtd
```
# create vm
Open `virtual machine manager` app.

