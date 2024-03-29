---
title: How to change GDM or SDDM to LightDM
description: 
published: true
date: 2023-02-18T17:05:56.351Z
tags: 
editor: markdown
dateCreated: 2023-02-18T16:56:36.859Z
---

First, we will install everything necessary to have lightdm in our system. To do this, from the terminal:

```
sudo pacman -S lightdm lightdm-gtk-greeter rebornos-lightdm-gtk-greeter-images lightdm-gtk-greeter-settings
```

Then edit `lightdm-gtk-greeter.conf`:
```
sudo nano /etc/lightdm/lightdm-gtk-greeter.conf
```
and add
```ini
[greeter]
theme-name = Flat-Plat-Blue
icon-theme-name = Flat-Remix-Green
background = /usr/share/pixmaps/rebornos.jpg
default-user-image = /usr/share/pixmaps/avatar.png
```
Save (<kbd>Ctrl</kbd> <kbd>S</kbd>) and exit (<kbd>Ctrl</kbd> <kbd>X</kbd>).

**NOTE 1:** If KDE or GNOME is installed with ISO `RebornOS-2020.08.22-x86_64.iso` or newer, the above steps are unnecessary as it will be installed by cnchi.

**NOTE 2:** In the case of installing LightDM in KDE, there is one more step to follow:

We must create the **ksplashrc** file in `~/.config`. This is done from the terminal with (In this case we will **not use sudo**):

```
nano ~/.config/ksplashrc
```

Inside copy the following:

```ini
[KSplash]
Engine=none
Theme=None
```

Save (<kbd>Ctrl</kbd> <kbd>S</kbd>) and exit (<kbd>Ctrl</kbd> <kbd>X</kbd>).
<br>
## On GNOME

We will have to disable `gdm`, and enable `lightdm`. To do this, from the terminal:

```
sudo systemctl disable gdm
sudo systemctl enable lightdm
```

If we want to disable LightDM, and re-enable GDM to use GNOME as it comes by default, then from the terminal:

```
sudo systemctl disable lightdm
sudo systemctl enable gdm
```

## On KDE

We will have to disable `sddm`, and enable `lightdm`. To do this, from the terminal:

```
sudo systemctl disable sddm
sudo systemctl enable lightdm
```

If we want to disable LightDM, and re-enable SSDM to use KDE as it comes by default, then from the terminal:

```
sudo systemctl disable lightdm
sudo systemctl enable sddm
```

**NOTE:** When KDE is started with lightdm, the KDE panel is unconfigured. To correct it, we can remove the panel, and add a default panel.