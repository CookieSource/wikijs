---
title: Troubleshooting
description: Solutions to common problems during installation
published: true
date: 2022-11-02T13:32:14.601Z
tags: troubleshooting
editor: markdown
dateCreated: 2021-09-23T12:57:05.025Z
---

# Common Issues

Here you can find a list of issues that can arise during installation

## No network connectivity during install (while connected to the internet)

**Problem:**  
The installer cannot find you’re connected to the internet.  
**Solution**

```plaintext
sudo sed -i 's/1.1.1.1/1.0.0.127/g' /usr/share/cnchi/src/misc/extra.py
```

## Installer won't start

Make sure you're connected to the internet and then open a terminal and type this command.

```plaintext
bash refresh-keys.sh
```

## Undefined installation failures

Please run the installer from the terminal with this command.

```plaintext
sudo cnchi-installer
```