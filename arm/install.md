---
title: ARM Installation
description: Short article on how to install RebornOS ARM onto your SBC's
published: true
date: 2023-02-19T18:53:47.956Z
tags: arm, installation
editor: markdown
dateCreated: 2023-02-18T16:53:21.676Z
---

# Offline installation on a RPI 3b+/4b/400
![](https://de.mirror.rebornos.org/pics/)
Create your storage medium using these [steps](/en/arm/requirements#flashing-the-image-onto-the-storage-medium-from-a-pc). After that turn off your device and plug in the HDMI cable, storage medium and the power cable.
When you boot successfully, you will be greeted with the ISO Welcome app:
![Firstboot](https://de.mirror.rebornos.org/pics/firstboot.jpg)
You *do not* need to be connected to the internet for offline installation. But there is no problem if the internet is on.
Click on the big *Install Offline* button with the image of a green icon:
![Welcome app](https://de.mirror.rebornos.org/pics/welcomeready.jpg)
The busy indicator turns red to indicate that the app is busy checking updates and/or updating the installer:
![Welcome app busy](https://de.mirror.rebornos.org/pics/welcomeworking.jpg)
When the update process completes (if the update toggle was on), the indicator turns back to green color. You can either click on Console, or resize the window at any time to see details about what the app is doing. The below indicates that the update is complete and the installer is launched:
![Welcome app with console](https://de.mirror.rebornos.org/pics/welcomeconsole.jpg)
## 1. Welcome
When the installer finally shows up, you will be greeted with a Welcome page where you can select your language:
![Calamares welcome page](https://de.mirror.rebornos.org/pics/calamaresfirst.jpg)
If you want to change the language, click on American English for the list of languages to show up choose your language and click Next.
## 2. Location
On the location page, you can either click on the world map to choose your time zone, or select it manually by clicking on the menus for Region and Zone:
![Calamares location page](https://de.mirror.rebornos.org/pics/calamareslocale.jpg)
You can also select the system language and local from the buttons on the right side. When you are done, click Next.
## 3. Keyboard
If you have a non-US keyboard layout, you can select it here:
![Calamares keyboard page](https://de.mirror.rebornos.org/pics/calamareskey.jpg)
## 4. Users
Here you can select a username and password for use on your RebornOS. You can also choose to reuse the same password for the root account:
![Calamares users page](https://de.mirror.rebornos.org/pics/calamaresuser.jpg)
## 5. Summary
Here, you should verify that the changes shown by the installer do not inadvertently delete or erase your important data. You can also check that the installer is only making the changes that you intended:
![Calamares summary page](https://de.mirror.rebornos.org/pics/calamaresfinish.jpg)
Proceed when you are sure that the info that you entered is correct.
## 6. Install
When the installation starts, you will be greeted with a slideshow:
![Calamares install slideshow](https://de.mirror.rebornos.org/pics/calamaresslide.jpg)
On the right side of the progress bar, is a small button that you can click to show the logs instead of the slideshow:
![Calamares install log](https://de.mirror.rebornos.org/pics/calamaresconsole.jpg)
If the installer unfortunately fails, you will be shown a dialog window describing what the problem is, and it asks whether you want to upload the logs to an online paste server. We recommend you to upload the logs so that you can share the URL with support for diagnosing your issue.
![Calamares error](https://de.mirror.rebornos.org/pics/calamareserror.jpg)
If you chose to upload the logs you will be shown a URL that you can share with anyone who offers support in order to diagnose the error.
## 7. Finish
When the installer finishes click on Restart System to reboot immediately:
![Calamares finished page](https://de.mirror.rebornos.org/pics/calamaresfinisha.jpg)
# Online installation on a RPI 3b+/4b/400
![](https://de.mirror.rebornos.org/pics/)
Create your storage medium using these [steps](/en/arm/requirements#flashing-the-image-onto-the-storage-medium-from-a-pc). After that turn off your device and plug in the HDMI cable, storage medium and the power cable.
When you boot successfully, you will be greeted with the ISO Welcome app:
![Firstboot](https://de.mirror.rebornos.org/pics/firstboot.jpg)
You *do not* need to be connected to the internet for offline installation. But there is no problem if the internet is on.
Click on the big *Install online* button with the image of a blue icon:
![Welcome app](https://de.mirror.rebornos.org/pics/welcomeready.jpg)
The busy indicator turns red to indicate that the app is busy checking updates and/or updating the installer:
![Welcome app busy](https://de.mirror.rebornos.org/pics/welcomeworking.jpg)
When the update process completes (if the update toggle was on), the indicator turns back to green color. You can either click on Console, or resize the window at any time to see details about what the app is doing. The below indicates that the update is complete and the installer is launched:
![Welcome app with console](https://de.mirror.rebornos.org/pics/welcomeconsole.jpg)
## 1. Welcome
When the installer shows up, you will be greeted with a Welcome page where you can select your language:
![Install welcome](https://de.mirror.rebornos.org/pics/online/onlinefirst.jpg)
If you want to change the language, click on American English for the list of languages to show up choose your language and click Next.
## 2. Location
On the location page, you can either click on the world map to choose your time zone, or select it manually by clicking on the menus for Region and Zone:
![Region and Zone](https://de.mirror.rebornos.org/pics/online/onlinelocale.jpg)
You can also select the system language and local from the buttons on the right side. When you are done, click Next.
## 3. Keyboard
If you have a non-US keyboard layout, you can select it here:
![Language select](https://de.mirror.rebornos.org/pics/online/onlinekey.jpg)
## 4. Desktops/WMs
Here you can select any desktops or window managers that you would like to install with RebornOS. For a single selection, you can just click on the option you want to choose and it gets selected:
![Desktop WM select](https://de.mirror.rebornos.org/pics/online/onlineDE.jpg)
Multiple selection requires you to hold down the Ctrl or Shift keys after selecting the first option.


> Warning: Selecting multiple desktops is not recommended. Desktops tend to overwrite themes and other files from one another, causing visual artifacts that break the appearance. Select multiple desktops only if you know what you are doing.
{.is-warning}
## 5. Advanced

> Note: You can skip the Advanced page safely and go to the next partition page. Read this section if you want more control on what packages are installed or not installed.
{.is-info}

The Advanced page consists of a heirarchy of categories and packages. The appear collapsed by default:
![Advanced default collapsed](https://de.mirror.rebornos.org/pics/online/onlineextra.jpg)
> Note: Please do not be tempted to check entire categories for installation. This will result in bloating of your install and will end up using a lot of your storage. It is always a good idea to expand each category to select the smallest subset of packages that you want to install.
{.is-info}

> Warning: We recommend beginners to not change anything in the Minimal Base category. It contains basic applications required for your RebornOS to function properly. Removing packages from here may result in a poorly functioning installation.
{.is-warning}

Desktop related packages are always at the end. You can expand the desktop category to see a Curated list, and sometimes Exhaustive and Miscellaneous lists.

The curated package list for each desktop contains the recommended packages which are a good fit for most people. The exhaustive list usually contains all possible desktop related packages mentioned in the Arch Wiki if you want to add more things to your desktop.

You can choose which parts of RebornOS base and apps to install. However, we recommend to only change the RebornOS Apps if you want to, and leave the RebornOS Base category unchanged.
## 6. Users
Here you can select a username and password for use on your RebornOS. You can also choose to reuse the same password for the root account:
![Calamares users page](https://de.mirror.rebornos.org/pics/online/onlineusers.jpg)
## 7. Summary
Here, you should verify that the changes shown by the installer do not inadvertently delete or erase your important data. You can also check that the installer is only making the changes that you intended:
![Install summary](https://de.mirror.rebornos.org/pics/online/onlinesummary.jpg)
Proceed only when you are sure that your data and partitions are going to be safe.
## 8. Install
When the installation starts, you will be greeted with a slideshow:
![Install and copy files](https://de.mirror.rebornos.org/pics/online/onlineslide.jpg)
On the right side of the progressbar, is a small button that you can click to show the logs instead of the slideshow:
![Install show progress](https://de.mirror.rebornos.org/pics/online/onlineconsole.jpg)
If the installer unfortunately fails, you will be shown a dialog window describing what the problem is, and it asks whether you want to upload the logs to an online paste server. We recommend you to upload the logs so that you can share the URL with support for diagnosing your issue.
## 9. Finish
When the installer finishes, you can either close the installer to stay on the live ISO, or click on Restart System to reboot immediately:
![Calamares finished page](/arm/finish_online.jpg)