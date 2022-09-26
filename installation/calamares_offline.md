---
title: [Guide] [Offline Installation] An Introduction to the Calamares-based RebornOS ISO and Installer
description: 
published: true
date: 2022-09-26T22:20:20.765Z
tags: installer, calamares, install, offline
editor: markdown
dateCreated: 2022-09-26T22:13:59.892Z
---

> **Note**: This guide is for **Offline Installation**. For the *Online Installation* guide, [click here](https://wiki.rebornos.org/en/installation/calamares_online).

> **Note**: This guide assumes that you have already downloaded the Calamares-based RebornOS ISO, prepared a bootable live USB/DVD, and enabled booting from that USB/DVD in your boot priority settings (BIOS).

When you first boot from the live ISO, you will see a menu of various boot modes:
![grub](upload://coO9uspYZ1vBUzsSHJTcnddY10O.png)
Choose the first option (which is the default). If it fails to boot, choose the second option. And if that fails too, choose the third option. 

When you boot successfully, you will be greeted with the ISO Welcome app: 
![001](upload://pA0iblYR7F4DSK1dntjhtJWAvSr.jpeg)

You *do not* need to be connected to the internet for offline installation. But there is no problem if the internet is on. 

Click on the big *Install Offline* button with the image of a green icon: 
![002](upload://so6qdmfSTCTfsI300JOwl5jtfqG.png)
The busy indicator turns red to indicate that the app is busy checking updates and/or updating the installer
![003](upload://252zzGYhEAQv2KfqFzAdsN1WIT1.png)
When the update process completes (if the update toggle was on), the indicator turns back to green color. You can either click on *Console*, or resize the window at any time to see details about what the app is doing. The below indicates that the update is complete and the installer is launched: 
![004](upload://Ad4E9u6FKRgijYNy0MxRD5Qlp55.png)
> **Note**: Due to the *partition* module taking time to load, the installer may take anywhere from a few seconds to a few minutes to show up. Please be patient while this is happening. You can run `tail -f ~/install.log` on a terminal to see more details about the launch if you suspect it is taking too long, or that something is wrong.

## 1. Welcome 
When the installer finally shows up, you will be greeted with a Welcome page where you can select your language: 
![001o](upload://zoHLpSGt7p59jOuVjbKrMxHYIwl.png)
If you want to change the language, click on *American English* for the list of languages to show up: 
![002o](upload://58MKdXUUwCBCX6s1gnf28DWuTPQ.png)
Choose your language and click Next.

## 2. Location
On the location page, you can either click on the world map to choose your time zone, or select it manually by clicking on the menus for *Region* and *Zone*: 
![003o](upload://iEue12AqeROIk8Tkq4GpK4eDDIX.png)
You can also select the system language and local from the buttons on the right side. When you are done, click Next.

## 3. Keyboard

If you have a non-US keyboard layout, you can select it here: 
![004o](upload://c0hr9w0pdQUvlkaqoc0HMq01xqW.png)

## 4. Partitions

The partitions page allows you to select whether and how to change your storage to install RebornOS. Depending on the current state of your storage medium, the options you get may differ from the screenshot below
![005o](upload://onFczmapVKJv49SH7ihNxPdM1s4.png)
If you choose to modify your partitions, you will see options to select a filesystem of your choice. 

## 5. Users

Here you can select a *username* and *password* for use on your RebornOS. You can also choose to reuse the same password for the `root` account: 
![006o](upload://ez3helPtCgNAkdRVTDkUUECtdkS.png)

## 6. Summary

Here, you should verify that the changes shown by the installer do not inadvertently delete or erase your important data. You can also check that the installer is only making the changes that you intended: 
![007o](upload://4f1zjZAXZ4yrM7WkCmP543WRRx5.png)
Proceed only when you are sure that your data and partitions are going to be safe. 

## 7. Install

When the installation starts, you will be greeted with a slideshow:
![008o](upload://sd8eJsHPZqLss19e6tz1p1bvfV2.png)
On the right side of the progress bar, is a small button that you can click to show the logs instead of the slideshow: 
![009o](upload://rFOPzy5ST9L9yksVDS9K0kPbvR4.png)

If the installer unfortunately fails, you will be shown a dialog window describing what the problem is, and it asks whether you want to upload the logs to an online paste server. We recommend you to upload the logs so that you can share the URL with support for diagnosing your issue. 
![031](upload://fOIopdW9htMo8Y5OiRnXObvhKCq.png)
If you chose to upload the logs you will be shown a URL that you can share with anyone who offers support in order to diagnose the error: 
![032](upload://oZgAlF2dBwHaLxV0sIoMl3Y6Pp1.png)

## 8. Finish

When the installer finishes, you can either close the installer to stay on the live ISO, or click on Restart System to reboot immediately: 
![010o](upload://uLYu5W1ZmKJXXpScdG78072VkqM.png)

## (Optional) Upload Logs

Sometimes, it is a good idea to save logs even when the installation shows as successful. This is usually done for testing purposes. Ensure that the internet is on and working, and then run `upload-logs` on a terminal at any time (even after the installation completed) before rebooting, to upload the logs to a paste server and obtain the URL that you may share with anyone offering support:
![034](upload://rWG068VusgInTrsos37pdWk4WLL.png)

The log file is present at `~/install.log` if you would like to read it without uploading:
![035](upload://6yy64mvxi9jzqotr1D0xs5GV4L8.png)