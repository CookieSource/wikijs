---
title: Universal package management 
description: Universal package solution on RebornOS, Snap, Flatpak & Appimage
published: true
date: 2022-03-27T11:13:59.016Z
tags: customization, snap, flatpak, appimage, universal package management
editor: markdown
dateCreated: 2021-10-16T12:40:24.070Z
---

# Universal package management.

RebornOS has support for all the major package solutions on Linux.

## Snap

Canonical universal package solution

### How to install Snap

Install the `snapd `package via the command line or use a graphical store like [Pamac](/en/howto/pamac)

```plaintext
sudo pacman -S snapd snapd-glib
```

enable the snap service.

```plaintext
sudo systemctl enable --now snapd
```

### How to use Snap

From the terminal or via a graphical store like [Pamac](/en/howto/pamac)

```plaintext
sudo snap install appname
```

## Flatpak

### How to install Flatpak

Install the `flatpak `package via the command line or use a graphical store like [Pamac](/en/howto/pamac)

```plaintext
sudo pacman -S flatpak
```

It may be necessary to reboot after installing Flatpak

### How to use Flatpak

**By using** [**flathub**](https://flathub.org/)

Navigate on Flathub to an app you want and click install.

It may be required to click the downloaded file.

**From the terminal installing an app**

```plaintext
sudo flatpak install appname
```

**Deleting an app from the terminal**

```plaintext
sudo flatpak uninstall appname
```

or use a graphical store like [Pamac](/en/howto/pamac)

## Appimage

### How to install Appimage

install the `appimagelauncher `via the command line or use a graphical store like [Pamac](/en/howto/pamac)

```plaintext
sudo pacman -S appimagelauncher
```

Download [https://appimage.github.io/AppImageUpdate/](https://appimage.github.io/AppImageUpdate/)

Double click it and select integrate and run.

### How to use Appimage

Download an Appimage of your choice and double click it

![](/screenshot.png)

Choose whether you want to integrate the app into your system or use it once.