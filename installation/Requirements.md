---
title: Requirements
description: Requirements for installing
published: true
date: 2022-01-10T04:42:09.348Z
tags: requirements
editor: markdown
dateCreated: 2021-09-23T12:39:54.260Z
---

# Requirements

Here you can find the requirements for RebornOS

**Required specification table**

|     |     |     |
| --- | --- | --- |
| Requirements | Minimum specification | Recommended specification |
| CPU | 1.2 GHz dual core | 2.1 GHz quad core |
| RAM | 2 Gigabyte  (GB) | 4 Gigabyte (GB) |
| Storage | 20 Gigabyte (GB) | 40 Gigabyte (GB) or more |
| Installation medium | CD/DVD or USB 4 gigabyte (GB) | CD/DVD or USB 4 gigabyte (GB) or more |
| Internet connection | Recommended, Not required | Recommended, Not required |

# Preparing an install medium

Download the latest RebornOS ISO [link](https://www.rebornos.org/downloads)

Download the latest version of Balena Etcher for your Operating system [link](https://www.balena.io/etcher/)

If you want to burn to burn to a CD/DVD you cannot use Balena Etcher. Please use a program to burn DVD's in order to accomplish that!

## Windows

1.  Install Balena Etcher (If you need extra help we also have a [Youtube](https://youtu.be/xyKsJ-5MkKw) video available [here](https://youtu.be/xyKsJ-5MkKw)
2.  Start Balena Etcher from your start menu
3.  Select the RebornOS ISO you downloaded
4.  Select the USB drive you inserted
5.  Flash!

## MacOS

1.  Install Balena Etcher
2.  Run Balena Etcher from finder
3.  Select the RebornOS ISO you downloaded
4.  Select the USB drive you inserted
5.  Flash!

## Linux

1.  Make the Balena Etcher Appimage executable and then run it
2.  Select the RebornOS ISO that you downloaded
3.  Select the inserted USB
4.  Flash!

# Booting from install medium

## Windows 

1.  we need to enter the BIOS/UEFI of your system to change a few settings. Most BIOS/UEFI systems use a special key that lets you choose the boot medium, and that lets you choose the BIOS configuration screen (where you can select the boot order). Depending on the BIOS, these keys are: Escape, F1, F2, F8, F10, F11, F12, or Delete. Usually, this information is briefly displayed during boot
2.  Once you're in the BIOS/UEFI screen you need to find secure boot and turn it off.
3.  You need to set your USB key as the first option to boot from
4.  Reboot
5.  If everything went correctly you should see the RebornOS boot screen
6.  Select NVIDIA if you have an NVIDIA graphics card or select boot install medium if you don't!

## macOS

Note this guide is for old Macs if you got a mac newer than 2014. Please look up a tutorial for your model by using a searcher like [Google](https://www.google.com)! or [DDG](https://www.duck.com)

1.  Hold you alt or option key after hearing the boot-up sound
2.  Select the USB you inserted from the menu that appears
3.  Select NVIDIA if you have an NVIDIA graphics card or select boot install medium if you don't!

## Linux

1.  Boot from the USB stick
2.  Select NVIDIA if you have an NVIDIA graphics card or select boot install medium if you don't!

[Click this link to go to the installation guide /en/installation/cnchi](/en/installation/cnchi)