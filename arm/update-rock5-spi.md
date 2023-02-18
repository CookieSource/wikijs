---
title: How to update the SPI flash on Radxa Rock 5A or 5B
description: How to update the SPI flash on Rock 5a or 5b
published: true
date: 2023-02-18T19:59:18.184Z
tags: arm, rock 5
editor: markdown
dateCreated: 2023-02-18T16:53:43.308Z
---

In order to prepare the Rock 5B to be able to boot from the NVMe SSD several steps need to be performed.
These steps are to be performed when the Rock 5B is booted into Linux (i.e. from eMMC or microSD card) with network connectivity.
If you don't have network connectivity then just copy the image files to other external media (i.e. USB stick) to be able to access them.
- Obtain both the Rock 5 zero and the 5B SPI image files from the Radxa links below.
`wget https://dl.radxa.com/rock5/sw/images/others/zero.img.gz`
`wget https://dl.radxa.com/rock5/sw/images/loader/rock-5b/release/rock-5b-spi-image-g49da44e116d.img`
- Extract the zero SPI image.
`gzip -d zero.img.gz`
- Write the zero SPI image to the target device using the `dd` command.
`sudo dd if=zero.img of=/dev/mtdblock0`
- Wait for around 5 minutes for the command to complete, then check for the correct md5 validation checksum.
`sudo md5sum /dev/mtdblock0`
```
2c7ab85a893283e98c931e9511add182
```
- Next, use the Rock 5b SPI image and write it to the target device.
`sudo dd if=rock-5b-spi-image-g49da44e116d.img of=/dev/mtdblock0`
- Again, wait for about5 minutes for the command to complete, then check for the correct md5 validation checksum.
`sudo md5sum /dev/mtdblock0`
```
46de85de37b8e670883e6f6a8bb95776
```
- Once verified,
`sync`
`reboot`
 
# Update SPI flash on Radxa Rock 5A
**Coming soon**