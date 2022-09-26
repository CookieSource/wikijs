---
title: [Guide] [Online Installation] An Introduction to the Calamares-based RebornOS ISO and Installer
description: 
published: true
date: 2022-09-26T22:11:55.995Z
tags: calamares, online, installer, install
editor: markdown
dateCreated: 2022-09-26T22:11:55.995Z
---

> **Note**: This guide is for **Online Installation**. For the *Offline Installation* guide, [click here](https://wiki.rebornos.org/en/installation/calamares_offline). 

> **Note**: This guide assumes that you have already downloaded the Calamares-based RebornOS ISO, prepared a bootable live USB/DVD, and enabled booting from that USB/DVD in your boot priority settings (BIOS).

When you first boot from the live ISO, you will see a menu of various boot modes:
![grub](upload://coO9uspYZ1vBUzsSHJTcnddY10O.png)
Choose the first option (which is the default). If it fails to boot, choose the second option. And if that fails too, choose the third option. 

When you boot successfully, you will be greeted with the ISO Welcome app: 
![001](upload://pA0iblYR7F4DSK1dntjhtJWAvSr.jpeg)

Ensure that you connected to the internet (WiFi or ethernet). Look for the appropriate settings in one of the buttons near the bottom right corner of your screen.

> **Note**: Leave the *Update* toggle as it is (which is *on* by default), to update to the latest version of the installer before launching. 

Click on the big *Install Online* button with the image of a blue icon: 
![002](upload://so6qdmfSTCTfsI300JOwl5jtfqG.png)
The busy indicator turns red to indicate that the app is busy checking updates and/or updating the installer 
![003](upload://252zzGYhEAQv2KfqFzAdsN1WIT1.png)
When the update process completes, the indicator turns to green color. You can either click on *Console*, or resize the window at any time to see details about what the app is doing. The below indicates that the update is complete and the installer is launched: 
![004](upload://Ad4E9u6FKRgijYNy0MxRD5Qlp55.png)
> **Note**: Due to the *partition* module taking time to load, the installer may take anywhere from a few seconds to a few minutes to show up. Please be patient while this is happening. You can run `tail -f ~/install.log` on a terminal to see more details about the launch if you suspect it is taking too long, or that something is wrong.

## 1. Welcome 
When the installer finally shows up, you will be greeted with a Welcome page where you can select your language: 
![005](upload://kIGw2T9FH7ZMYYn9Zi3Wen3cn4d.png)
If you want to change the language, click on *American English* for the list of languages to show up: 
![006](upload://xhnL49u23GYK8J6b0IgsKIgpgtF.png)
Choose your language and click Next.

## 2. Location
On the location page, you can either click on the world map to choose your time zone, or select it manually by clicking on the menus for *Region* and *Zone*: 
![007](upload://6iAPflTKsyPy7CfHz8S7djqwXi8.png)
You can also select the system language and local from the buttons on the right side. When you are done, click Next.

## 3. Keyboard

If you have a non-US keyboard layout, you can select it here: 
![008](upload://sZBWTWzihCqlGug3r3rux14R6mT.png)

## 4. Desktops/WMs

Here you can select any desktops or window managers that you would like to install with RebornOS. For a single selection, you can just click on the option you want to choose and it gets selected: 
![009](upload://gbvUDRNeYx7IxtgOYJXtaSYE8M0.png)

Multiple selection requires you to hold down the `Ctrl` or `Shift` keys after selecting the first option:
> **Warning**: Selecting multiple desktops is *not* recommended. Desktops tend to overwrite themes and other files from one another, causing visual artifacts that break the appearance. Select multiple desktops **only** if you know what you are doing. 

![010](upload://pHuDH9UhzYCPiurKEwa6dy8461E.png)

## 5. Advanced

> **Note**: You can skip the Advanced page safely and go to the next partition page. Read this section if you want more control on what packages are installed or not installed. 

The *Advanced* page consists of a heirarchy of categories and packages. The appear collapsed by default:
![011](upload://xYLrhhqA5j9wVCRUNu4mrskj8tC.png)

> **Note**: Please *do not* be tempted to check entire categories for installation. This will result in bloating of your install and will end up using a lot of your storage. It is always a good idea to expand each category to select the smallest subset of packages that you want to install. 

> **Warning**: We recommend beginners to not change anything in the *Minimal Base* category. It contains basic applications required for your RebornOS to function properly. Removing packages from here may result in a poorly functioning installation. 

Desktop related packages are always at the end. You can expand the desktop category to see a *Curated* list, and sometimes *Exhaustive* and *Miscellaneous* lists: 
![012](upload://hmkbPvw0GzuzmYjzumSQH6DZAyt.png)
The curated package list for each desktop contains the recommended packages which are a good fit for most people. The exhaustive list usually contains all possible desktop related packages mentioned in the *Arch Wiki* if you want to add more things to your desktop. 

If you do not want certain packages to be installed with the desktop of your choice, expand the *Curated* category and uncheck to remove any packages from the list: 
![013](upload://b5UkWwrhk67aH2rL2UwtmWfe37D.png)

You can choose which parts of RebornOS base and apps to install. However, we recommend to only change the *RebornOS Apps* if you want to, and leave the *RebornOS Base* category unchanged. 
![014](upload://qm8wJYzvmlSSOlkR3y4HKMIBdhV.png)

Third party drivers (like Nvidia proprietary drivers) can be found under the *Backend System* category as shown: 
![015](upload://huuyIjJZqL1zupvhPAgpFXIkZpD.png)

## 6. Partitions

The partitions page allows you to select whether and how to change your storage to install RebornOS. Depending on the current state of your storage medium, the options you get may differ from the screenshot below
![016](upload://ckaXXWnczdw4cONDrG3zQCVLaMb.png)

If you choose to modify your partitions, you will see options to select a filesystem of your choice. 

## 7. Users

Here you can select a *username* and *password* for use on your RebornOS. You can also choose to reuse the same password for the `root` account: 
![022](upload://zMJ8Hk2hm0xJyHhrte48sXLwaHH.png)

## 8. Summary

Here, you should verify that the changes shown by the installer do not inadvertently delete or erase your important data. You can also check that the installer is only making the changes that you intended: 
![023](upload://fOQPgUdknYPoWWRErNMkWBhY2Cc.png)
Proceed only when you are sure that your data and partitions are going to be safe. 

## 9. Install

When the installation starts, you will be greeted with a slideshow:
![024](upload://qKBhD7xItCWWvXjPvqyMdyjkzB9.png)
On the right side of the progressbar, is a small button that you can click to show the logs instead of the slideshow: 
![030](upload://l7d8foeCYtHICm6N27ukBG2UBEe.png)

If the installer unfortunately fails, you will be shown a dialog window describing what the problem is, and it asks whether you want to upload the logs to an online paste server. We recommend you to upload the logs so that you can share the URL with support for diagnosing your issue. 
![031](upload://fOIopdW9htMo8Y5OiRnXObvhKCq.png)
If you chose to upload the logs you will be shown a URL that you can share with anyone who offers support in order to doagnose the error: 
![032](upload://oZgAlF2dBwHaLxV0sIoMl3Y6Pp1.png)

## 10. Finish

When the installer finishes, you can either close the installer to stay on the live ISO, or click on Restart System to reboot immedietly: 
![033](upload://xM53Sd0gLpG6h5FotjRhHJSfJJX.png)

## (Optional) Upload Logs

Sometimes, it is a good idea to save logs even when the installation shows as successful. This is usually done for testing purposes. Ensure that the internet is on and working, and then run `upload-logs` on a terminal at any time (even after the installation completed) before rebooting, to upload the logs to a paste server and obtain the URL that you may share with anyone offering support:
![034](upload://rWG068VusgInTrsos37pdWk4WLL.png)

The log file is present at `~/install.log` if you would like to read it without uploading:
![035](upload://6yy64mvxi9jzqotr1D0xs5GV4L8.png)