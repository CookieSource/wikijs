---
title: Dual-boot Windows with RebornOS
description: Instructions for restoring the Windows entry in Grub while dual-booting Windows with RebornOS
published: true
date: 2022-12-18T07:23:56.535Z
tags: grub, bootloader, dual-boot, windows
editor: markdown
dateCreated: 2021-09-17T08:28:59.266Z
---

Once you have installed RebornOS, you may see that there is no Windows entry present in Grub. You can restore it by following the below steps:

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
	sudo nano /etc/default/grub
	```
	Uncomment/edit/add this entry:
	```
	GRUB_DISABLE_OS_PROBER=false
	```
	> 	Make sure that there is no `#` before the entry. 
	{.is-info}

	Save the file and exit(<small><kbd>Control</kbd> <kbd>S</kbd></small>, <small><kbd>Control</kbd> <kbd>X</kbd></small>).

3. Regenerate grub entries 
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

4. Reboot.