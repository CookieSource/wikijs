---
title: How to Install RebornOS onto a Mekotronics device.
description: How to Install RebornOS onto a Mekotronics device.
published: true
date: 2023-02-21T18:13:43.530Z
tags: arm
editor: markdown
dateCreated: 2023-02-18T18:40:03.325Z
---

# Install RebornOS onto a Mekotronics Device

Currently only the following devices are supported:

-   R58X
-   R58X-4G
-   R58S

## Preparation 

Download the latest RebornOS image for your ARM device from [here](https://rebornos.org/download-arm).  
Then extract it so that you are left with a .img file.

### Put your device in maskrom mode.

Connect the USB-C cable to your PC and to the device, then with a toothpick hold the RECOVERY button then press the RESET button.  
On R58X

![r58x.png](/arm/r58x.png)

On R58X-4G

![r58x-4g.png](/arm/r58x-4g.png)

On R58S (mini pc)

![r58s.png](/arm/r58s.png)

## Write image to eMMC

Instructions on how to write the image files to the eMMC:

### From Linux

-   [ ] After you have put your device into maskrom mode, verify this from your system.

```plaintext
sudo rkdeveloptool ld
```

Output should look something similar to this:

> DevNo=1 Vid=0x2207,Pid=0x350b,LocationID=801 Maskrom

-   [ ] Download [rk3588\_spl\_loader\_v1.09.111.bin](/arm/rk3588_spl_loader_v1.09.111.bin) then run:

```plaintext
sudo rkdeveloptool db ~/Downloads/rk3588_spl_loader_v1.09.111.bin
```

> If you get "The device does not support this operation!" re-plug the device.

-   [ ] Write the image you downloaded.

```plaintext
sudo rkdeveloptool wl 0 ~/Downloads/RebornOS-ARM-r58x-2023-01-14.img
```

> Replace the path and name with the path where the extracted image is.

-   [ ] Reboot the device:

```plaintext
sudo rkdeveloptool rd
```

### Install your preferred Desktop and Packages:

You can follow the installation guide [here.](/arm/install)

###   
  
From Windows

**TODO**