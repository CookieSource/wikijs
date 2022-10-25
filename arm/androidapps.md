---
title: How to use Android apps on your ARM SBC
description: 
published: true
date: 2022-10-25T09:02:34.642Z
tags: 
editor: markdown
dateCreated: 2022-10-23T12:49:03.402Z
---

# Installation

First begin by opening a terminal and installing the necessary packages.

```
sudo pacman -Sy android-appsupport
```

Then, edit `/etc/modules-load.d/anbox.conf` with a text editor (for example, `nano`)

```
sudo nano /etc/modules-load.d/anbox.conf
```

Paste the following into the file:

```
binder_linux
ashmem_linux
```

Then use <kbd>Ctrl</kbd> <kbd>S</kbd> and <kbd>Ctrl</kbd> <kbd>X</kbd> to save and exit.

Enable the container service:

```
sudo systemctl enable --now anbox-container-manager.service
```
Reboot!

Then you can open the Anbox app

# Install apps from an .apk file

Install the `android-tools` package:

```plaintext
sudo pacman -S android-tools
```

Then you can install your app using:
```
adb install ./path/to/app.apk
```