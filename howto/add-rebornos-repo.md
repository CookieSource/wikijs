---
title: How to add the RebornOS repository
description: rebornos repo
published: true
date: 2022-03-21T17:36:39.978Z
tags: repository repo
editor: markdown
dateCreated: 2021-09-23T23:55:22.765Z
---

# How to add the RebornOS repository

Let's see how to add the RebornOS repository to a distribution based on Arch linux.

First, we will edit the file pacman.conf:

First, you must edit the **pacman.conf** file to add the RebornOS repository. You can add the RebornOS repository at the end of the file, or place it after the Arch Linux `#[testing]` repository (the testing repository is disabled by default). This last way to install it (after the Arch Linux testing repository) is the default installation that RebornOS performs.

So, edit the file:
```
sudo nano /etc/pacman.conf
```

Then, add the following lines to the end of the file (**NOTE**: RebornOS installs its repository by default ***BEFORE*** the others.):

```ini
[Reborn-OS]
SigLevel = Optional TrustAll
Include = /etc/pacman.d/reborn-mirrorlist
```

**NOTE:** If the RebornOS repository is being added instead of the Antergos repository (if they still have it in your system), there will be an additional step, which will be to comment on the Antergos repository, as follows. Look for the lines:

```ini
[antergos]
SigLevel = PackageRequired
Include = /etc/pacman.d/antergos-mirrorlist
```

... and comment on them:

```ini
# [antergos]
# SigLevel = PackageRequired
# Include = /etc/pacman.d/antergos-mirrorlist
```

Save the file (<kbd>Ctrl</kbd> <kbd>S</kbd>) and exit (<kbd>Ctrl</kbd> <kbd>X</kbd>).

Now, add the mirrors of RebornOS. To do this, create the file ***reborn-mirrorlist*** as follows:

```
sudo nano /etc/pacman.d/reborn-mirrorlist
```

Inside, copy the following lines:

```ini
# RebornOS repo: repo.rebornos.org
Server = https://repo.rebornos.org/RebornOS/


##### Start OSDN mirrors #####
# OSDN RebornOS Repository 1
Server = https://mirrors.dotsrc.org/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# OSDN RebornOS Repository 2
Server = https://mirrors.tuna.tsinghua.edu.cn/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# OSDN RebornOS Repository 3
Server = https://ftp.iij.ad.jp/pub/osdn.jp/storage/g/r/re/rebornos/repo/RebornOS/

# OSDN RebornOS Repository 4
Server = https://mirrors.bfsu.edu.cn/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# OSDN RebornOS Repository 5
Server = https://mirror.liquidtelecom.com/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# OSDN RebornOS Repository 6
Server = https://ftp.jaist.ac.jp/pub/sourceforge.jp/storage/g/r/re/rebornos/repo/RebornOS/

# OSDN RebornOS Repository 7
Server = http://ftp.halifax.rwth-aachen.de/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# OSDN RebornOS Repository 8
Server = http://mirroronet.pl/pub/mirrors/sourceforge.jp/storage/g/r/re/rebornos/repo/RebornOS/

# OSDN RebornOS Repository 9
Server = https://ftp.acc.umu.se/mirror/osdn.net/storage/g/r/re/rebornos/repo/RebornOS/

# OSDN RebornOS Repository 10
Server = http://osdn.mirror.constant.com/storage/g/r/re/rebornos/repo/RebornOS/

# OSDN RebornOS Repository 11
Server = http://mirror.math.princeton.edu/pub/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# OSDN RebornOS Repository 12
Server = https://plug-mirror.rcac.purdue.edu/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# OSDN RebornOS Repository 13
Server = https://mirrors.gigenet.com/OSDN/storage/g/r/re/rebornos/repo/RebornOS/

# OSDN RebornOS Repository 14
Server = https://openbsd.c3sl.ufpr.br/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# OSDN RebornOS Repository 15
Server = http://osdn.ip-connect.vn.ua/storage/g/r/re/rebornos/repo/RebornOS/
##### End OSDN mirrors #####


##### Start Sourceforge mirrors #####
# Sourceforge 1
Server = http://razaoinfo.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/

# Sourceforge 2
Server = http://versaweb.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/

# Sourceforge 3
Server = http://phoenixnap.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/

# Sourceforge 4
Server = http://newcontinuum.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/

# Sourceforge 5
Server = http://downloads.sourceforge.net/rebornos/r/RebornOS/

# Sourceforge 6
Server = http://cfhcable.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/

# Sourceforge 7
Server = http://astuteinternet.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/

# Sourceforge 8
Server = http://vorboss.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/

# Sourceforge 9
Server = http://freefr.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/

# Sourceforge 10
Server = http://netcologne.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS

# Sourceforge 11
Server = http://netix.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/

# Sourceforge 12
Server = http://excellmedia.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/

# Sourceforge 13
Server = http://liquidtelecom.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/

# Sourceforge 14
Server = https://jztkft.dl.sourceforge.net/project/rebornos/r/RebornOS/

# Sourceforge 15
Server = http://sourceforge.mirror.iweb.com/project/rebornos/r/RebornOS/

# Sourceforge 16
Server = https://deac-riga.dl.sourceforge.net/project/rebornos/r/RebornOS/

# Sourceforge 17
Server =  http://tenet.dl.sourceforge.net/project/rebornos/r/RebornOS/

# Sourceforge 18
Server = https://nchc.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/

# Sourceforge 19
Server = https://kent.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/

# Sourceforge 20
Server = https://jaist.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/
##### End Sourceforge mirrors #####

# mirror.arctic.lol (Finland)
Server = http://mirror.arctic.lol/RebornMirror/

# RebornOS mirror.clarkson.edu
Server = https://mirror.clarkson.edu/RebornOS/
```

Save the file (***Ctrl + o***), and exit (***Ctrl + x***).

Then from the terminal:

```
sudo chmod 644 /etc/pacman.d/reborn-mirrorlist
```

Another way to create the mirrorlist file is by copying and pasting the following in the terminal:

```
sudo wget https://gitlab.com/rebornos-team/rebornos-special-system-files/mirrors/reborn-mirrorlist/-/raw/master/reborn-mirrorlist /etc/pacman.d/reborn-mirrorlist
sudo chmod 644 /etc/pacman.d/reborn-mirrorlist
```

What will have to be done next, is to acquire the public pgp keys from the RebornOS repository. To do this, download the following file:

```
wget https://repo.rebornos.org/RebornOS/rebornos-keyring-20210512-1.2-any.pkg.tar.zst
```

Then, manually install the downloaded file. This is done with:

```
sudo pacman -U rebornos-keyring-20210512-1.2-any.pkg.tar.zst
```

Why is this procedure necessary? This is because all the files in the RebornOS repository are signed with one of the keys in this file (which correspond to the users in charge of maintaining the repository).

Then update the repositories:

```
sudo pacman -Syy
```

Once this procedure is finished, we can update our system, or install something existing in the RebornOS repositories.