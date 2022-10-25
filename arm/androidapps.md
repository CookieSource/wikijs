---
title: How to use Android apps on your ARM SBC
description: 
published: true
date: 2022-10-25T08:55:33.932Z
tags: 
editor: markdown
dateCreated: 2022-10-23T12:49:03.402Z
---

# Installation

First begin by opening a terminal and installing the necessary packages.

```plaintext
sudo pacman -Sy android-appsupport
```

Then add the following to `/etc/modules-load.d/anbox.conf` using `nano`

```plaintext
sudo nano /etc/modules-load.d/anbox.conf
```

Paste the following into this file:

```plaintext
binder_linux
ashmem_linux
```

Then use CTRL + S and CTRL + X to save and exit.

Enable the service:

```plaintext
sudo systemctl enable --now anbox-container-manager.service
```

Reboot!

Then you can open the anbox app

# Install apps from an .apk file

Install `android-tools` package using your preferred package manager or by using pacman:

```plaintext
sudo pacman -S android-tools
```

Then you can install your app using:

```plaintext
adb install ./path/to/app.apk
```