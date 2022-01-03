---
title: Dual-Boot Windows with RebornOS
description: Instructions for restoring the Windows entry in Grub while dual-booting Windows with RebornOS
published: true
date: 2021-09-23T13:04:38.911Z
tags: grub, bootloader, dual-boot, windows
editor: markdown
dateCreated: 2021-09-17T08:28:59.266Z
---

# Dual-Boot Windows with RebornOS

Once you have installed RebornOS, you may see that the Windows entry is not present in Grub. You can restore it by following the below steps on **RebornOS**:

1. Install `os-prober` and `ntfs-3g` if not already present.
```
sudo pacman -S --needed os-prober ntfs-3g 
```

2. Run `os-prober` to check if it recognizes Windows
```
sudo os-prober
```

3. Permit grub to use os-prober
```
sudo pacman -S --needed gedit
sudo gedit /etc/default/grub
```
Uncomment/edit/add this entry:
```
GRUB_DISABLE_OS_PROBER=false
```
Make sure that there is no `#` before the entry. 
Save the file and exit. 

3. Regenerate grub entries 
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

4. Reboot
```
reboot
```






