---
title: How to run RebornOS arm in a VM on an x64-bit pc
description: Short article on how to run RebornOS ARM on an x86_64 pc using QEMU 
published: true
date: 2022-11-15T20:41:24.133Z
tags: 
editor: markdown
dateCreated: 2022-11-14T15:15:37.027Z
---

The qcow2 image file is a prebuilt RebornOS ARM QEMU / Virtual Manager image.  Having the ability to RebornOS ARM VM, will allow more flexibility for development, testing and running ARM apps.

# Download image
https://github.com/RebornOS-Developers/qemu-images/releases/latest
Download the appropriate image: `RebornOS-ARM-generic-YYYY-MM-DD.qcow2`
# Install required qemu virt-manager dependencies
```sh
sudo pacman -S qemu virt-viewer libvirt virt-manager qemu-desktop qemu-system-aarch64 edk2-armvirt
```
# Enable libvirtd service
```sh
sudo systemctl enable --now libvirtd
```
# Create VM
Open `Virtual Machine Manager` application.

Follow step-by-step images to create and configure the ARM VM.

1. Click the button for new VM or `File > New Virtual Machine`:
![virtman-new-vm-button.png](/how-to/run-rebornos-arm/virtman-new-vm-button.png)
1. Choose `Import existing disk image` and select the architecture `aarch64`:
![virtman-create-new-virt-machine.png](/how-to/run-rebornos-arm/virtman-create-new-virt-machine.png)

1. Find and select the RebornOS ARM image you downloaded:
![virtman-browse-local-storage.png](/how-to/run-rebornos-arm/virtman-browse-local-storage.png)
![virtman-step2-select-storage-vol-2022-11-14_17-16-39.png](/how-to/run-rebornos-arm/virtman-step2-select-storage-vol-2022-11-14_17-16-39.png)
![virtman-locate-select-disk-image.png](/how-to/run-rebornos-arm/virtman-locate-select-disk-image.png)
1. Type in `linux2022` and select `Generic Linux 2022` for the operating system:
![virtman-choose-image-2022-11-14_17-17-19.png](/how-to/run-rebornos-arm/virtman-choose-image-2022-11-14_17-17-19.png)
1. Then allocate a minimum of 2048MB RAM and 2 VCPUs:
![virtman-step3-memory-cpu-alloc-2022-11-14_17-17-31.png](/how-to/run-rebornos-arm/virtman-step3-memory-cpu-alloc-2022-11-14_17-17-31.png)
1. Name the VM and check `Customize configuration before install`:
![virtman-step4-name-customize-2022-11-14_17-17-55.png](/how-to/run-rebornos-arm/virtman-step4-name-customize-2022-11-14_17-17-55.png)
1. Next, add the additional hardware:
![virtman-add-hardware-after-creation.png](/how-to/run-rebornos-arm/virtman-add-hardware-after-creation.png)
1. Spice server

1. Mouse support
1. Keyboard
1. Finish
1. Launch VM

