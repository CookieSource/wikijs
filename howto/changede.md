---
title: How to install/change/remove desktop environment.
description: How to change install or remove desktop environment.
published: true
date: 2022-01-05T17:25:07.990Z
tags: 
editor: markdown
dateCreated: 2021-12-31T13:12:44.612Z
---

# Introduction

List of available desktop environment (as of 31/12/2021)  
 

-   Budgie (rebornos-cosmic-budgie)
-   Cinnamon (rebornos-cosmic-cinnamon)
-   Cutefish (rebornos-cosmic-cutefish)
-   Deepin (rebornos-cosmic-deepin)
-   Enlightenment (rebornos-cosmic-enlightenment)
-   Gnome (rebornos-cosmic-gnome)
-   i3 (rebornos-cosmic-i3)
-   KDE (rebornos-cosmic-kde)
-   lxde-gtk3 (rebornos-cosmic-lxde)
-   LXQt (rebornos-cosmic-lxqt)
-   MATE (rebornos-cosmic-mate)
-   Openbox RebornOS
-   Regolith (rebornos-cosmic-regolith)
-   UKUI
-   XFCE (rebornos-cosmic-xfce)

> Note: There are some DEs that are incompatible with some display mangers (gdm sddm lightDM) refer to [How to change gdm or sddm to lightdm](https://wiki.rebornos.org/en/howto/sddm-to-lightdm)

# Installing a DE

There are two ways of installing a DE on your PC, manually or with our app [RebornOS Fire](https://wiki.rebornos.org/en/apps/RebornOSFire).  
Installing a desktop environment manually can be done with: (Look at [Introduction](https://wiki.rebornos.org/en/howto/changede#introduction) to see the package name)

```plaintext
pacman -S reborn-cosmic-DE
```

# Removing a DE

Removing a DE cant be done through our app yet™ but can be done manually with:

```plaintext
sudo pacman -R reborn-cosmic-DE
```