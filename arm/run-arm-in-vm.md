---
title: How to run RebornOS arm in a VM on an x64-bit pc
description: Short article on how to run RebornOS ARM on an x86_64 pc using QEMU 
published: true
date: 2022-11-14T15:25:07.244Z
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

Use images to write a step by step guide

1. Click the button for new VM
1. Select the architecture `aarch64`
1. Find and select the RebornOS image you downloaded 
1. Then alocate a minimum of 2048MB RAM and 2VCPU's
1. Then add the aditional hardware
1. Spice server
1. Mouse support
1. Keyboard
1. Finish
1. Launch VM

