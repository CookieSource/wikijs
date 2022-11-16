---
title: How to run RebornOS arm in a VM on an x64-bit pc
description: Short article on how to run RebornOS ARM on an x86_64 pc using QEMU 
published: true
date: 2022-11-16T22:11:34.243Z
tags: 
editor: markdown
dateCreated: 2022-11-14T15:15:37.027Z
---

The qcow2 image file is a prebuilt RebornOS ARM QEMU / Virtual Manager image.  Having the ability to RebornOS ARM VM, will allow more flexibility for development, testing and running ARM apps.

# Download image
https://github.com/RebornOS-Developers/qemu-images/releases/latest
Choose and download the desired image: `RebornOS-ARM-generic-YYYY-MM-DD.qcow2`
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
1. Find and select the RebornOS ARM image downloaded:
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
1. Graphics Spice server support:
![virtman-graphics-hardware-settings-2022-11-14_17-18-53.png](/how-to/run-rebornos-arm/virtman-graphics-hardware-settings-2022-11-14_17-18-53.png)
1. Input Mouse support `EvTouch USB Graphics Tablet` :
![virtman-add-hardware-mouse-2022-11-14_17-19-15.png](/how-to/run-rebornos-arm/virtman-add-hardware-mouse-2022-11-14_17-19-15.png)
1. Keyboard:
![virtman-add-hardware-keyboard-2022-11-14_17-19-29.png](/how-to/run-rebornos-arm/virtman-add-hardware-keyboard-2022-11-14_17-19-29.png)
1. Finish the configuration.
1. Launch VM.
## Additional info
`virsh`
An interactive shell, and batch scriptable tool for performing management tasks on all libvirt managed domains, networks and storage. This is part of the libvirt core distribution.

To start the `default` network for the VM:
```$ sudo virsh net-start default```
To auto-start the `default` network after a reboot:
```$ sudo virsh net-autostart default```

Additional notes:
The above is only the minimal for getting the ARM VM up and running.  In order to tweak the settings or further configure QEMU Virtual Manager, additional information is available from the following links.

- Arch Linux QEMU Wiki - https://wiki.archlinux.org/title/QEMU
- Virt-Manager.org - https://virt-manager.org/
- libvirt.org - https://www.libvirt.org/
- RebornOS forum - https://rebornos.discourse.group/
