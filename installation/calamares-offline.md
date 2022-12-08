---
title: Install RebornOS offline
description: 
published: true
date: 2022-12-08T11:30:54.575Z
tags: installer, calamares, install, offline
editor: markdown
dateCreated: 2022-09-26T22:13:59.892Z
---

> **Note**: This guide is for **Offline Installation**. For the *Online Installation* guide, [click here](/en/installation/calamares-online).

> **Note**: This guide assumes that you have already downloaded the Calamares-based RebornOS ISO, prepared a bootable live USB/DVD, and enabled booting from that USB/DVD in your boot priority settings (BIOS).

When you first boot from the live ISO, you will see a menu of various boot modes:

![](/installer/offline/calamares-grub-menu.png)

Grub boot menu

  
Choose the first option (which is the default). If it fails to boot, choose the second option. And if that fails too, choose the third option.

When you boot successfully, you will be greeted with the ISO Welcome app:

![](/installer/offline/calamares-welcome.jpeg)

RebornOS Welcome

You *do not* need to be connected to the internet for offline installation. But there is no problem if the internet is on.

Click on the big *Install Offline* button with the image of a green icon:

![](/installer/offline/calamares-install-select-offline.png)

Install offline

The busy indicator turns red to indicate that the app is busy checking updates and/or updating the installer  
  
When the update process completes (if the update toggle was on), the indicator turns back to green color. You can either click on *Console*, or resize the window at any time to see details about what the app is doing. The below indicates that the update is complete and the installer is launched:

![](/installer/offline/calamares-install-red-indicator.png)

Red busy indicator

> **Note**: Due to the *partition* module taking time to load, the installer may take anywhere from a few seconds to a few minutes to show up. Please be patient while this is happening. You can run `tail -f ~/install.log` on a terminal to see more details about the launch if you suspect it is taking too long, or that something is wrong.

## 1\. Welcome

When the installer finally shows up, you will be greeted with a Welcome page where you can select your language:

![](/installer/offline/calamares-install-welcome.png)

Install welcome

If you want to change the language, click on *American English* for the list of languages to show up:

![](/installer/offline/calamares-install-language-select.png)

Install language select

Choose your language and click Next.

## 2\. Location

On the location page, you can either click on the world map to choose your time zone, or select it manually by clicking on the menus for *Region* and *Zone*:  
 

![](/installer/offline/calamares-install-region-select.png)

Region and Zone select

  
You can also select the system language and local from the buttons on the right side. When you are done, click Next.

## 3\. Keyboard

If you have a non-US keyboard layout, you can select it here:

![](/installer/offline/calamares-install-keyboard-select.png)

Keyboard select and test

## 4\. Partitions

The partitions page allows you to select whether and how to change your storage to install RebornOS. Depending on the current state of your storage medium, the options you get may differ from the screenshot below:

![](/installer/offline/calamares-install-partitions.png)

Partitioning

If you choose to modify your partitions, you will see options to select a filesystem of your choice.

## 5\. Users

Here you can select a *username* and *password* for use on your RebornOS. You can also choose to reuse the same password for the `root` account:

![](/installer/offline/calamares-install-users.png)

User account and passwords

## 6\. Summary

Here, you should verify that the changes shown by the installer do not inadvertently delete or erase your important data. You can also check that the installer is only making the changes that you intended:

![](/installer/offline/calamares-install-summary.png)

Install summary

Proceed only when you are sure that your data and partitions are going to be safe.

## 7\. Install

When the installation starts, you will be greeted with a slideshow:

![](/installer/offline/calamares-install-copying-files.png)

Install to disk

On the right side of the progress bar, is a small button that you can click to show the logs instead of the slideshow:

![](/installer/offline/calamares-install-copying-files-show-logs.png)

Install log displayed

If the installer unfortunately fails, you will be shown a dialog window describing what the problem is, and it asks whether you want to upload the logs to an online paste server. We recommend you to upload the logs so that you can share the URL with support for diagnosing your issue.

![](/installer/offline/calamares-installation-failed.png)

Install error

If you chose to upload the logs you will be shown a URL that you can share with anyone who offers support in order to diagnose the error:

![](/installer/offline/calamares-installation-failed-choose-upload.png)

Log upload link

## 8\. Finish

When the installer finishes, you can either close the installer to stay on the live ISO, or click on Restart System to reboot immediately:

![](/installer/offline/calamares-install-finish.png)

## (Optional) Upload Logs

Sometimes, it is a good idea to save logs even when the installation shows as successful. This is usually done for testing purposes. Ensure that the internet is on and working, and then run `upload-logs` on a terminal at any time (even after the installation completed) before rebooting, to upload the logs to a paste server and obtain the URL that you may share with anyone offering support:

![](/installer/offline/calamares-upload-logs.png)

upload-logs

The log file is present at `~/install.log` if you would like to read it without uploading:

![](/installer/offline/calamares-install.log-location.png)

install.log location