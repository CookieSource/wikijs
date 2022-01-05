---
title: How to install/change/remove desktop environment.
description: How to change install or remove desktop environment.
published: true
date: 2022-01-05T17:30:09.831Z
tags: 
editor: markdown
dateCreated: 2021-12-31T13:12:44.612Z
---

# Introduction

List of available desktop environments (as of 5/1/2022)
 

-   Budgie (rebornos-cosmic-budgie)
-   Cinnamon (rebornos-cosmic-cinnamon)
-   Cutefish (rebornos-cosmic-cutefish)
-   Deepin (rebornos-cosmic-deepin)
-   Enlightenment (rebornos-cosmic-enlightenment)
-   Gnome (rebornos-cosmic-gnome)
-   i3 (rebornos-cosmic-i3)
-   KDE (rebornos-cosmic-kde)
-   LXDE (rebornos-cosmic-lxde)
-   LXQt (rebornos-cosmic-lxqt)
-   MATE (rebornos-cosmic-mate)
-   Openbox (rebornos-cosmic-openbox)
-   Regolith (rebornos-cosmic-regolith)
-   UKUI (rebornos-cosmic-ukui)
-   XFCE (rebornos-cosmic-xfce)

> Note: There are some DEs that are incompatible with some display mangers (gdm, sddm and lightDM) refer to [How to change gdm or sddm to lightdm](https://wiki.rebornos.org/en/howto/sddm-to-lightdm)

# Installing a DE

There are two ways of installing a DE on RebornOS - in Terminal or with our app [RebornOS Fire](https://wiki.rebornos.org/en/apps/RebornOSFire).  
Installing a desktop environment manually can be done with: (Look at [Introduction](https://wiki.rebornos.org/en/howto/changede#introduction) to see the package name)

```
pacman -S <package name>
```

# Removing a DE

Removing a DE can't be done through our app yet but can be done manually with:

```
sudo pacman -R <package name>
```