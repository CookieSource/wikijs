---
title: How to use bauh package manager by Arnulf
description: How to use bauh
published: true
date: 2021-09-27T12:08:21.065Z
tags: package-manager, bauh
editor: markdown
dateCreated: 2021-09-25T15:24:19.711Z
---

# How to use bauh package manager by Arnulf

A first overview of the surface and use of bauh.

At the start, the data of the installed packages are first loaded and then displayed:

<p align="center">
<img src="https://i.imgur.com/B4IRw82.png">
</p>
By deactivating the Apps switch, all other packages are also displayed:

<p align="center">
<img src="https://i.imgur.com/TYuWj3S.png">
</p>

With the Type button you can choose between Reborn/Arch repository or the AUR repository to install programmes:

<p align="center">
<img src="https://i.imgur.com/JZDZ4N3.png?1">
</p>

With the category button you can select different categories:

<p align="center">
<img src="https://i.imgur.com/UY4VTe0.png">
</p>

The Refresh button takes you back to the beginning:

<p align="center">
<img src="https://i.imgur.com/PqS4GR3.png?1">
</p>

With the light bulb additional options for applications are displayed:

<p align="center">
<img src="https://i.imgur.com/o4suDGp.png">
</p>

With the colour palette you can select a theme:

<p align="center">
<img src="https://i.imgur.com/B02QOLi.png">
</p>

Use the gearwheel switch to enter configuration:

<p align="center">
<img src="https://i.imgur.com/JNNjw7w.png">
</p>

In the configuration you can make an enormous number of settings - here the Types module as an example.
Here you can decide what kind of repositories you want to include, only Arch or also Flatpak or AppImage:

<p align="center">
<img src="https://i.imgur.com/RuxpY8g.png">
</p>

The nice thing about bauh is that every button, except in the backup module, has an auxiliary button that displays a short description:

<p align="center">
<img src="https://i.imgur.com/IawVEnT.png">
</p>

In the hamburger menu there are several more important actions:

<p align="center">
<img src="https://i.imgur.com/NgRq2sX.png">
</p>

<p align="center">
<img src="https://i.imgur.com/OE6Jniz.png">
</p>

The AppImage button installs AppImage.
<br>
## Synchronize package databases  to update the package database and upgrade the system.

This is followed by the query whether the sources should be updated, which is equivalent to `sudo pacman -Syy`:

<p align="center">
<img src="https://i.imgur.com/UohCQYQ.png">
</p>

After clicking on yes, you will be redirected to the password query:

<p align="center">
<img src="https://i.imgur.com/CPiRiq9.png">
</p>

If the database is up to date, the possible updates are displayed:

<p align="center">
<img src="https://i.imgur.com/eZxNgft.png">
</p>

After pressing the upgrade button, the upgrade process is started:

<p align="center">
<img src="https://i.imgur.com/HIqeJys.png">
</p>

If you are using btrfs or zfs you can create a snapshot so that after an error you can revert to the state before the update:

<p align="center">
<img src="https://i.imgur.com/KxjFIWK.png">
</p>

After the packages have been loaded and installed, you will be asked if you want to restart the system:

<p align="center">
<img src="https://i.imgur.com/IEco0B2.png">
</p>

Restore resets all settings of bauh to the default values and cleans the cache of bauh.





