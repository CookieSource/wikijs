---
title: RebornOS for Raspberry Pi 4 4 GB beta for Test by arnulf
description: RebornOS for Raspberry Pi 4 4 GB beta
published: true
date: 2023-02-18T17:05:33.357Z
tags: arm, raspberry
editor: markdown
dateCreated: 2023-02-18T16:53:28.647Z
---

# RebornOS for Raspberry Pi 4 4 GB beta for Test by arnulf

Download the file by <a href="https://osdn.net/dl/rebornos/RebornOS-ARM-Installer-2.3.sh" target="_blank">clicking here</a>

To start the script please type :

```
sudo sh RebornOS-ARM-Installer-2.3.sh
```

...in the console. After entering the password, the script starts with the instruction to close all file managers.

<p align="center">
<img src="https://i.imgur.com/OT0O2wB.png">
</p>

Then you can choose between lxqt and xfce Desktop Enviroment:

<p align="center">
<img src="https://i.imgur.com/VYfS2d3.png">
</p>

In the next step select the SD card you want to install RebornOS on, I use a USB SD card adapter so the drive is declared as **/dev/sda** for a sdcard reader included your Computer use **/dev/mmcblk0** :

<p align="center">
<img src="https://i.imgur.com/PyqSzMP.png">
</p>

After the basic settings are made, the script partitions the SD card and formats it:

<p align="center">
<img src="https://i.imgur.com/UXGvW68.png">
</p>

The script now searches for a mirror from which to download the RebornOS. This file is over 3 GB in size and it takes time to load it:

<p align="center">
<img src="https://i.imgur.com/72JxrtJ.png">
</p>

After downloading the file, it is also unpacked and copied, which of course takes time given the size of the file:

<p align="center">
<img src="https://i.imgur.com/84t9Qq7.png">
</p>

The next steps are synchronising with, and resizing the SD card:

<p align="center">
<img src="https://i.imgur.com/6WUMaJk.png">
</p>

The script ends with the folowing message:

The default user is alarm with the password alarm The default root password is root.

