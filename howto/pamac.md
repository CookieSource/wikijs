---
title: How to use pamac
description: 
published: true
date: 2022-03-14T11:59:21.758Z
tags: pamac, package-manager
editor: markdown
dateCreated: 2021-09-23T23:46:33.452Z
---

Pamac is the package manager used in RebornOS, and created by Manjaro. In the version used by RebornOS, it has AUR and Flatpak support, and this application takes care of the installation, uninstallation, and system update tasks.

The main screen that will be displayed once this application is executed is the following:

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/pamac/-/raw/master/pamac-main.png">
</p>

In the upper left corner, you can access the search for pamac by clicking on the magnifying glass icon.

By default, it starts on the **Browse** screen, which allows us to view all the software available in the repositories used by the distribution (which are the Arch repositories, and RebornOS 'own repository).

Clicking on **Installed** above, we will see a list with all the software currently installed.

By clicking **Updates** at the top, pamac will check to see if there are any updates for your system.

In the **Sort by** button, pamac will display the information by: relevance, name, repository, size, or date, as selected.

In the menu on the left (under the magnifying glass) it is possible to access the list of applications by category, groups, and existing repositories in the distribution.

By selecting categories, you can see something similar to what the following screen shows:

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/pamac/-/raw/master/pamac-categories-menu.png">
</p>

Selecting groups, you can see something similar to what the following screen shows:

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/pamac/-/raw/master/pamac-groups-menu.png">
</p>

Selecting repositories, you can see something similar to what the following screen shows:

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/pamac/-/raw/master/pamac-repositories-menu.png">
</p>

***By default, pamac on RebornOS comes configured with only 1 parallel download, and with AUR and Flatpak support disabled. In addition, when selecting a file to install, pamac will automatically check if there is an update, and will add it to the selected download (this can be modified). Also, check if there is an update every 6 hours.***

Accessing the menu on the top right, we can access Software Mode, Refresh database, View History, Install Local Packages, Preferences, and About:

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/pamac/-/raw/master/pamac-menu.png">
</p>

By selecting **Software Mode**, pamac will automatically select the existing Categories menu on the left.

**Refresh databases** as its name implies, updates the database of all existing repositories.

**View History**, opens a terminal window, showing the activities carried out by pamac.

**Install Local Package**, it will open a file selection window, where you can search for a package locally that you want to install.

**Preferences** allows you to configure different pamac options.

**About** indicates the version in use of pamac, and some other information related to the application.


# Pamac configuration

When accessing the Preferences menu, the following screen is displayed (the user's password will be requested to access this menu):

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/pamac/-/raw/master/pamac-config-general.png">
</p>

**Check for updates** is, as its name implies, where the option for pamac to check for system updates is enabled or disabled.

***Updates check frequency*** is where you can set the elapsed time between each check performed by pamac to see if there are new updates. The options are: every 3 hours, every 6 hours, every 12 hours, once a week, and once a month.

***Automatically download updates*** is, as its name implies, what allows pamac to automatically download any updates that may exist.

Under **Downloads**, there is ***Parallel downloads***.  Is the number of parallel downloads with which pamac will be able to work. This value can be: 1, 2, 4, 6, 8, and 10.

Under **Cache**, there is ***Number of versions of each package to keep***, and it is where you can set the number of versions that may exist of the same package in the cache. this value can be: 0, 1, 2, 3, 4, and 5.

***Remove only the uninstalled packages***, is the option that will allow pamac to remove from its cache the packages that have been removed from its system.

By clicking on ***Advanced***, this other screen is accessed:

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/pamac/-/raw/master/pamac-config-advanced.png">
</p>

***Check available disk space*** allows you to check if the available disk space is sufficient to carry out the operation in progress.

***Remove unrequired dependencies*** removes the dependencies that are not used by any package.

***Do not check for updates when installing*** prevents that when we install a package, pamac checks and installs any update that may exist, in addition to installing the package selected by the user (this operation is done without asking).

***Enable downgrade*** enables the ability to downgrade a package.

***Ignored upgrades*** allows us to create a list of applications that we do not want to be updated.

By clicking on ***Third Party***, this other screen is accessed:

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/pamac/-/raw/master/pamac-config-third-party.png">
</p>

On this screen you can enable (or disable) AUR and Flatpak support, as desired.

# Using pamac from the terminal

The available pamac actions when executed from the terminal are the following:

```
  pamac --version     
  pamac --help, -h     [action]
  pamac search         [options] <package(s)>
  pamac list           [options] <package(s)>
  pamac info           [options] <package(s)>
  pamac install        [options] <package(s)>
  pamac reinstall      [options] <package(s)>
  pamac remove         [options] [package(s)]
  pamac checkupdates   [options]
  pamac update,upgrade [options]
  pamac clone          [options] <package(s)>
  pamac build          [options] [package(s)]
  pamac clean          [options]
```


**Searching Packages**

To search google-chrome:

```
pamac search -a google-chrome

chromedriver-beta                                                                                            89.0.4389.23-1  AUR 
    Standalone server that implements the W3C WebDriver standard (for google-chrome-beta)
chromedriver                                                                                                 89.0.4389.23-1  AUR 
    Standalone server that implements the W3C WebDriver standard (for google-chrome)
google-chrome-dev                                                                                            91.0.4469.4-2   AUR 
    The popular and trusted web browser by Google (Dev Channel)
google-chrome-beta                                                                                           90.0.4430.72-2  AUR 
    The popular and trusted web browser by Google (Beta Channel)
google-chrome                                                                           [Installed packages] 90.0.4430.72-2  Reborn-OS 
    The popular and trusted web browser by Google (Stable Channel)
```

**Installing Packages**

`pamac install <package>`. In this example, google chrome is installed from terminal:

```
pamac install google-chrome
```

***IMPORTANT:*** pamac, unlike pacman, will only install those packages that are not on your system. This means that if you already have google-chrome installed, pamac will not install it again.

If you want to install some AUR, you will need to use the `pamac build` command. Suppose the installation of ***clockify-desktop***:

```
pamac build clockify-desktop
```

**Removing Packages**

The `pamac remove` command is used interchangeably to remove a package from the repositories, or from the AUR. For example:

```
pamac remove google-chrome
```

**IMPORTANT:** It is extremely important that the user knows what they are doing when they delete something. Sometimes it can happen that an attempt is made to remove a package whose function is unknown, but which is perhaps an important part of the system, and as a result, it may end with an installation that no longer works.


**List all packages installed on your system**

Use `pamac list` to list all packages installed on your system:

```
pacman list -i
```

**Show detailed information of a package**

Use `pamac info` to see, for example, the detailed information of google-chrome:

```
pamac info google-chrome

Name                           : google-chrome
Version                        : 90.0.4430.72-2
Description                    : The popular and trusted web browser by Google (Stable Channel)
URL                            : https://www.google.com/chrome
License                        : custom:chrome
Repository                     : Reborn-OS
Installed size                 : 244,8 MB
Depends on                     : alsa-lib gtk3 libcups libxss libxtst nss
Optional dependencies          : pipewire: WebRTC desktop sharing under Wayland [Installed packages]
                                 kdialog: for file dialogs in KDE
                                 gnome-keyring: for storing passwords in GNOME keyring [Installed packages]
                                 kwallet: for storing passwords in KWallet
                                 libunity: for download progress on KDE
                                 ttf-liberation: fix fonts for some PDFs - CRBug #369991 [Installed packages]
                                 xdg-utils [Installed packages]
Packer                         : Unknown Packager
Building date                  : 15/04/21
Instalation date               : 15/04/21
Installation reason            : Explicitly installed
Signed                         : Yes`
```

**Updating the System**

Use `pamac checkupdates` to check for updates:

```
pamac checkupdates -a
```

Use `pamac upgrade` to update your system, including any AUR packages that may exist:

```
pamac upgrade -a
```

**NOTE:** upgrade and update in pamac are the same, and you can use them interchangeably.


**Working with orphaned packages**

To check for unnecessary packages (known as orphaned packages) on your system:

```
pamac list -o
```

And to remove these packages that are no longer used:

```
pamac remove -o
```


**Cleaning the Cache**

pamac, when installing new packages on your system, stores a copy of the files to be replaced, in a place known as cache memory. The number of copies stored here can be configured (see above, in pamac Configuration).

If you want to delete the contents of this cache:

```
pamac clean
```

There is an option to delete all versions of existing packages in the cache memory, but leaving the three most recent copies of them:

```
pamac clean --keep 3
```


**Other Useful Pamac Functions**

To find out if a certain file is owned by an application, you can use:

```
pamac search -f unrar
```

To force reinstall a package that already exists on your system:

```
pamac reinstall google-chrome
```

