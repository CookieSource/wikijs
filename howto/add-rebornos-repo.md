---
title: How to add the RebornOS repository
description: rebornos repo
published: true
date: 2023-07-16T08:54:18.071Z
tags: repository repo
editor: markdown
dateCreated: 2023-02-18T16:54:37.202Z
---

# How to add the RebornOS repository to Arch or an Arch-based distribution

## Updating the pacman configuration

First, we will edit the file pacman.conf:
You must edit the **pacman.conf** file to add the RebornOS repository. You can add the RebornOS repository at the end of the file, or place it after the Arch Linux `#[testing]` repository (which is disabled by default). This last way to install it (after the Arch Linux testing repository) is the default installation that RebornOS performs.
So, edit the file:

```sh
sudo nano /etc/pacman.conf
```

Then, add the following lines to the end of the file

> RebornOS installs its repository by default _before_ the others.
> {.is-info}

```ini
[Reborn-OS]
SigLevel = Optional TrustAll
Include = /etc/pacman.d/reborn-mirrorlist
```

## Getting the mirror list

Follow any one of the procedures give below to get a copy of latest mirror list from RebornOS.

### Downloading a copy from GitHub

RebornOS hosts a copy of the mirror list on GitHub, available in this [repository](https://github.com/RebornOS-Developers/rebornos-mirrorlist).

Execute this command to get a copy of the mirror list:

```sh
sudo wget https://raw.githubusercontent.com/RebornOS-Developers/rebornos-mirrorlist/main/reborn-mirrorlist /etc/pacman.d/reborn-mirrorlist
```

Fix the permissions on newly created file:

```sh
sudo chmod 644 /etc/pacman.d/reborn-mirrorlist
```

### Manually

```sh
sudo nano /etc/pacman.d/reborn-mirrorlist
```

Add the following content to the file:

```ini
# --> RebornOS Mirror List from 20230424-1 <-- #

# RebornOS repo: repo.rebornos.org - GEO Mirror
Server = https://repo.rebornos.org/RebornOS/

# RebornOS repo: nl-mirror.rebornos.org/RebornOS - NL Mirror (with redirection)
Server = https://nl-mirror.rebornos.org/RebornOS/

# Mirror 1:
Server = http://osdn.mirror.constant.com/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 2:
Server = https://mirrors.ocf.berkeley.edu/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 3:
Server = https://ftp.iij.ad.jp/pub/osdn.jp/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 4:
Server = https://ftp.jaist.ac.jp/pub/sourceforge.jp/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 5:
Server = http://ftp.halifax.rwth-aachen.de/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 6:
Server = http://mirroronet.pl/pub/mirrors/sourceforge.jp/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 7:
Server = https://ftp.acc.umu.se/mirror/osdn.net/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 8:
Server = http://194.71.11.163/mirror/osdn.net/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 9:
Server = http://mirror.math.princeton.edu/pub/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 10:
Server = https://openbsd.c3sl.ufpr.br/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 11:
Server = https://mirrors.dotsrc.org/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 12:
Server = https://free.nchc.org.tw/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 13:
Server = https://ftp.sunet.se/mirror/osdn.net/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 14:
Server = http://pumath.dl.osdn.jp/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 15:
Server = http://ftp.dk.xemacs.org/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 16:
Server = http://ftp.openbsd.dk/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 17:
Server = http://mirrors.gigenet.com/OSDN/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 18:
Server = https://plug-mirror.rcac.purdue.edu/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 19:
Server = http://osdn.ip-connect.vn.ua/storage/g/r/re/rebornos/repo/RebornOS/

# Mirror 20:
Server = https://mirror.liquidtelecom.com/osdn/storage/g/r/re/rebornos/repo/RebornOS/


# RebornOS mirror.clarkson.edu
Server = https://mirror.clarkson.edu/RebornOS/RebornOS/


# Sourceforge mirror with redirection
Server = https://sourceforge.net/projects/rebornos/files/r/RebornOS/
```

Save the file (`CTRL` + `S`) and exit (`CTRL` + `X`).

Now, fix the permissions on the newly created file:

```sh
sudo chmod 644 /etc/pacman.d/reborn-mirrorlist
```

## Getting the public keys

All packages in RebornOS repositories are signed with packager's key, you must have the public key on your machine to be able to verify and install packages from RebornOS repositories.

You can get all the keys in RebornOS keyring from the repository,

Download the keyring package from the repository:

```sh
wget https://repo.rebornos.org/RebornOS/rebornos-keyring.pkg.tar.zst
```

Then, manually install it using:

```sh
sudo pacman -U rebornos-keyring.pkg.tar.zst
```

## Synchronize pacman databases

Run a full upgrade to get package database from RebornOS repositories:

```sh
sudo pacman -Syyu
```

After you have completed this step, you should have a RebornOS repositories installed on your system.
