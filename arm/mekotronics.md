---
title: How to Install RebornOS onto a Mekotronics device.
description: How to Install RebornOS onto a Mekotronics device.
published: true
date: 2023-02-18T19:50:13.538Z
tags: arm
editor: markdown
dateCreated: 2023-02-18T18:40:03.325Z
---

# Write image to eMMC

Instructions on how to write the image to eMMC

## Prep

Download the latest image for your device from [here](https://rebornos.org/download-arm).  
Then extract it so that you are left with a .img file

Before beginning put your device in maskrom mode.  
Connect USB-C cable to your PC to the device then with a toothpick hold the RECOVERY button then press the RESET button  
On R58X  
 

![r58x.png](/arm/r58x.png)

  
On R58X-4G  
 

![r58x-4g.png](/arm/r58x-4g.png)

  
On R58S (mini pc)  
 

![r58s.png](/arm/r58s.png)

## From Windows

**TODO**

## From Linux

1.  After you have put your device check if your pc finds it.

```plaintext
sudo rkdeveloptool ld
```

Output should look something similar to this

> DevNo=1 Vid=0x2207,Pid=0x350b,LocationID=801 Maskrom

1.  Download [rk3588\_spl\_loader\_v1.09.111.bin](/arm/rk3588_spl_loader_v1.09.111.bin) then run:

```plaintext
sudo rkdeveloptool db ~/Downloads/rk3588_spl_loader_v1.09.111.bin
```

> If you get "The device does not support this operation!" replug the device!

1.  Then write the image you downloaded.

```plaintext
sudo rkdeveloptool wl 0 ~/Downloads/RebornOS-ARM-r58x-2023-01-14.img
```

> Replace the path and name with the path where the extracted image is.

1.  Reboot the device

```plaintext
sudo rkdeveloptool rd
```

1.  Install your preffered Desktop and Packages

You can follow the install guide [here](/arm/install)