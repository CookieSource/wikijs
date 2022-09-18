---
title: ARM Installation
description: Short article on how to install RebornOS ARM onto your SBC's
published: true
date: 2022-09-18T10:05:35.256Z
tags: installation, arm
editor: markdown
dateCreated: 2022-09-17T18:58:51.418Z
---

# Offline installation on a RPI 3b+/4b/400
![](https://repo.liketraps.com/pics/)
Create your storage medium using these [steps](/en/arm/requirements#flashing-the-image-onto-the-storage-medium-from-a-pc). After that turn off your device and plug in the HDMI cable, storage medium and the power cable.

When you boot successfully, you will be greeted with the ISO Welcome app:
![Firstboot](https://repo.liketraps.com/pics/firstboot.jpg)
You *do not* need to be connected to the internet for offline installation. But there is no problem if the internet is on.

Click on the big *Install Offline* button with the image of a green icon:
![Welcome app](https://repo.liketraps.com/pics/welcomeready.jpg)

The busy indicator turns red to indicate that the app is busy checking updates and/or updating the installer:
![Welcome app busy](https://repo.liketraps.com/pics/welcomeworking.jpg)

When the update process completes (if the update toggle was on), the indicator turns back to green color. You can either click on Console, or resize the window at any time to see details about what the app is doing. The below indicates that the update is complete and the installer is launched:
![Welcome app with console](https://repo.liketraps.com/pics/welcomeconsole.jpg)

1. Welcome

When the installer finally shows up, you will be greeted with a Welcome page where you can select your language:
![Calamares welcome page](https://repo.liketraps.com/pics/calamaresfirst.jpg)

If you want to change the language, click on American English for the list of languages to show up choose your language and click Next.

2. Location

On the location page, you can either click on the world map to choose your time zone, or select it manually by clicking on the menus for Region and Zone:
![Calamares location page](https://repo.liketraps.com/pics/calamareslocale.jpg)

You can also select the system language and local from the buttons on the right side. When you are done, click Next.

3. Keyboard

If you have a non-US keyboard layout, you can select it here:
![Calamares keyboard page](https://repo.liketraps.com/pics/calamareskey.jpg)

4. Users

Here you can select a username and password for use on your RebornOS. You can also choose to reuse the same password for the root account:
![Calamares users page](https://repo.liketraps.com/pics/calamaresuser.jpg)

5. Summary

Here, you should verify that the changes shown by the installer do not inadvertently delete or erase your important data. You can also check that the installer is only making the changes that you intended:
![Calamares summary page](https://repo.liketraps.com/pics/calamaresfinish.jpg)

Proceed  when you are sure that the info that you entered is correct.

6. Install

When the installation starts, you will be greeted with a slideshow:
![Calamares install slideshow](https://repo.liketraps.com/pics/calamaresslide.jpg)

On the right side of the progress bar, is a small button that you can click to show the logs instead of the slideshow:
![Calamares install log](https://repo.liketraps.com/pics/calamaresconsole.jpg)

If the installer unfortunately fails, you will be shown a dialog window describing what the problem is, and it asks whether you want to upload the logs to an online paste server. We recommend you to upload the logs so that you can share the URL with support for diagnosing your issue.
![Calamares error](https://repo.liketraps.com/pics/calamareserror.jpg)

If you chose to upload the logs you will be shown a URL that you can share with anyone who offers support in order to diagnose the error.

7. Finish

When the installer finishes click on Restart System to reboot immediately:
![Calamares finished page](https://repo.liketraps.com/pics/calamaresfinisha.jpg)