---
title: Rate-Mirrors
description: Rank mirrors to speed up downloads from the repositories
published: true
date: 2023-02-18T17:19:26.172Z
tags: rate-mirrors, mirrors, pacman, refresh-mirrors-rebornos, refresh
editor: markdown
dateCreated: 2023-02-18T16:52:49.596Z
---

# How to install Rate-Mirrors

You can install Rate-Mirrors with

```plaintext
sudo pacman -S refresh-mirrors
```

# How to use Rate-Mirrors

Here's several of the ways you can use Rate-Mirrors on RebornOS

## Desktop entry

Open the **Refresh Mirrors** app. The text and icon may look like the below image:

![Screenshot from 2021-08-05 23-05-20](https://aws1.discourse-cdn.com/free1/uploads/rebornos/original/1X/8ba24aa1c698f00d79bf68d521c4979fcb84efa6.png)

Enter your password at the prompt and the rate-mirrors tool will run on a terminal with pre-selected options. In the end, it will refresh your **Arch Linux** and **RebornOS** mirrors to provide you the fastest update/install speed you can get.

## RebornOS Welcome

Launch the *RebornOS Welcome* application, Click on the `Utilities` tab on the bottom-left, and click on the `Refresh Pacman Mirrors` button as shown below:

![Screenshot from 2021-08-06 00-00-40](https://aws1.discourse-cdn.com/free1/uploads/rebornos/optimized/1X/634e1b524e321c3ebe27debee919389319da5c73_2_585x500.png)

Enter your password at the prompt and the rate-mirrors tool will run on a terminal with pre-selected options. In the end, it will refresh your Arch Linux and RebornOS mirrors to provide you the fastest install/update speed you can get.

## Systemd service

Just like how `reflector` does, we offer a Systemd service if you would like to run `rate-mirrors` every time you boot. to enable it, run the command

```plaintext
sudo systemctl enable refresh-mirrors.service
```

If you would also like to run the tool once now while also enabling it to run at boot, run

```plaintext
sudo systemctl enable --now refresh-mirrors.service
```

Enabling the systemd service using the above commands will run the [rate-mirrors](https://github.com/westandskif/rate-mirrors) tool every time you boot, with pre-selected options. In the end, it will refresh your **Arch Linux** and **RebornOS** mirrors to provide you the fastest update/install speed you can get.

## From the terminal

Run the `rate-mirrors` command to refresh **RebornOS** mirrors. Below is an example:

```plaintext
sudo rate-mirrors --concurrency=16 --per-mirror-timeout=3000 --allow-root --save=/etc/pacman.d/reborn-mirrorlist rebornos
```

Run the `rate-mirrors` command to refresh **Arch Linux** mirrors. Below is an example:

```plaintext
sudo rate-mirrors --protocol=https --allow-root --save=/etc/pacman.d/mirrorlist arch
```