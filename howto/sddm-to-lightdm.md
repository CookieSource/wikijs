---
title: How to change gdm or sddm to lightdm
description: sddm to lightdm
published: true
date: 2021-12-28T12:33:03.826Z
tags: 
editor: markdown
dateCreated: 2021-09-25T15:43:25.528Z
---

# How to change gdm or sddm to lightdm



First, we will install everything necessary to have lightdm in our system. To do this, from the terminal:

```
sudo pacman -S lightdm lightdm-gtk-greeter rebornos-lightdm-gtk-greeter-images lightdm-gtk-greeter-settings
```

Then we will customize the access. To do this, from the terminal:

```
sudo echo "[greeter]" >> /etc/lightdm/lightdm-gtk-greeter.conf
sudo echo "theme-name = Flat-Plat-Blue" >> /etc/lightdm/lightdm-gtk-greeter.conf
sudo echo "icon-theme-name = Flat-Remix-Green" >> /etc/lightdm/lightdm-gtk-greeter.conf
sudo echo "background = /usr/share/pixmaps/rebornos.jpg" >> /etc/lightdm/lightdm-gtk-greeter.conf
sudo echo "default-user-image = /usr/share/pixmaps/avatar.png" >> /etc/lightdm/lightdm-gtk-greeter.conf
```

**NOTE 1:** If KDE or GNOME is installed with ISO RebornOS-2020.08.22-x86_64.iso or newer, the above steps are unnecessary as it will be installed by cnchi.

**NOTE 2:** In the case of installing lightdm in PLASMA, there is one more step to follow:

We must create the **ksplashrc** file in **~/.config**. This is done from the terminal with (In this case we will **not use sudo**):

```
nano ~/.config/ksplashrc
```

Inside copy the following:

```
[KSplash]
Engine=none
Theme=None
```

Save (Ctrl + o) and exit (Ctrl + x).
<br>
## In the case of changing gdm to lightdm if we use GNOME:

We will have to disable gdm, and enable lightdm. To do this, from the terminal:

```
sudo systemctl disable gdm
sudo systemctl enable lightdm
```

If we want to disable lightdm, and re-enable gdm to use GNOME as it comes by default, then from the terminal:

```
sudo systemctl disable lightdm
sudo systemctl enable gdm
```

## In the case of changing sddm to lightdm if we use KDE:

We will have to disable sddm, and enable lightdm. To do this, from the terminal:

```
sudo systemctl disable sddm
sudo systemctl enable lightdm
```

If we want to disable lightdm, and re-enable sddm to use KDE as it comes by default, then from the terminal:

```
sudo systemctl disable lightdm
sudo systemctl enable sddm
```

**NOTE:** When start KDE with lightdm, the KDE panel is unconfigured. To correct it, we can remove this panel, and add a default panel.

