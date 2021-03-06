---
title: Requirements
description: Here you can find the requirements for RebornOS
published: true
date: 2022-04-13T06:13:24.371Z
tags: requirements
editor: markdown
dateCreated: 2021-09-23T12:39:54.260Z
---

**Required specification table**

|     |     |     |
| --- | --- | --- |
| Requirements | Minimum specification | Recommended specification |
| CPU | 1.2 GHz dual core | 2.1 GHz quad core |
| RAM | 2 GB | 4 GB |
| Storage | 20 GB | 40 GB or more |
| Installation medium | CD/DVD or USB 4 GB | CD/DVD or USB 4 GB or more |
| Internet connection | Recommended, Not required | Recommended, Not required |

# Preparing an install medium

If you want to burn to burn to a CD/DVD you cannot use Balena Etcher. Please use another program to burn DVD's in order to accomplish that!

[Download](https://rebornos.org/downloads) the latest RebornOS ISO

1.  Download the latest version of [Balena Etcher](https://balena.io/etcher) for your OS
2.  Open the app
3.  Select the RebornOS ISO you downloaded
4.  Select the inserted USB
5.  Flash!

We also have a video tutorial to do it on Windows: [RebornOS - How to create install media](https://youtu.be/xyKsJ-5MkKw)

# Booting from install medium

## Windows 

1.  We need to enter the BIOS/UEFI of your system to change a few settings. Most BIOS/UEFI systems use a special key that lets you choose the boot medium, and that lets you choose the BIOS configuration screen (where you can select the boot order). Depending on the BIOS, these keys are: Esc, F1, F2, F8, F10, F11, F12, or Delete. Usually, this information is briefly displayed during boot
2.  Once you're in the BIOS/UEFI screen you need to find secure boot and turn it off.
3.  You need to set your USB key as the first option to boot from
4.  Reboot
5.  If everything went correctly you should see the RebornOS boot screen
6.  Select NVIDIA if you have an NVIDIA graphics card or select boot install medium if you don't!

## macOS

1.  Reboot.
2.  Press and hold the Alt or Option key before hearing the startup sound.
3.  Select the USB you inserted from the menu that appears.
4.  Select NVIDIA if you have an NVIDIA graphics card or select boot install medium if you don't!

## Linux

1.  Boot from the USB stick.
2.  Select NVIDIA if you have an NVIDIA graphics card or select boot install medium if you don't!

Installation guide: [installation/cnchi](/en/installation/cnchi)