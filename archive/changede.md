---
title: How to install and remove desktop environments
description: 
published: true
date: 2023-03-16T10:37:05.267Z
tags: 
editor: markdown
dateCreated: 2023-02-18T16:55:03.931Z
---

# Introduction
List of available desktop environments (as of April 2022)
- Budgie (rebornos-cosmic-budgie)
- Cinnamon (rebornos-cosmic-cinnamon)
- Cutefish (rebornos-cosmic-cutefish)
- Deepin (rebornos-cosmic-deepin)
- GNOME (rebornos-cosmic-gnome)
- i3 (rebornos-cosmic-i3)
- KDE (rebornos-cosmic-kde)
- LXDE (rebornos-cosmic-lxde)
- LXQt (rebornos-cosmic-lxqt)
- MATE (rebornos-cosmic-mate)
- Openbox (rebornos-cosmic-openbox)
- Regolith (rebornos-cosmic-regolith)
- UKUI (rebornos-cosmic-ukui)
- Xfce (rebornos-cosmic-xfce)
> Note: There are some DEs that are incompatible with some display mangers (GDM, SSDM and lightDM) refer to [How to change GDM or SDDM to LightDM](/howto/sddm-to-lightdm)
# Installing a DE
There are two ways of installing a DE on RebornOS - in Terminal or with our app [RebornOS Fire](/apps/rebornosfire).
Installing a desktop environment manually can be done with: (Look at [Introduction](#introduction) to see the package name)
```
sudo pacman -S <package name>
```
# Removing a DE
Removing a DE can't be done through our app yet but can be done manually with:
```
sudo pacman -Rncs <package name>
```