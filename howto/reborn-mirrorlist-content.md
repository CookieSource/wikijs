---
title: How to know the content of the reborn-mirrorlist file
description: reborn-mirrorlist content
published: true
date: 2023-02-18T17:05:48.202Z
tags: reborn-mirrorlist
editor: markdown
dateCreated: 2023-02-18T16:56:22.933Z
---

The idea of this post is to indicate the contents of the reborn-mirrorlist file, and to indicate any problems that may exist in that file.

We indicate the change to be made in the `reborn-mirrorlist file`, so that the system works without problems.

**There are currently 37 active mirrors from the RebornOS repository.**

If you want to update the content of your reborn-mirrorlist file, then copy and paste the following content, replacing what previously existed in the file:

```
sudo nano /etc/pacman.d/reborn-mirrorlist
```

Then, you will have to copy and paste the following (If you don't want to change the file, don't edit it, and just read the mirrors listing):

```
# --> RebornOS Mirrorlist from 20210702-1 <-- #

# RebornOS repo: repo.rebornos.org
Server = https://repo.rebornos.org/RebornOS

##### Start OSDN mirrors #####
# OSDN RebornOS Repository 1
Server = https://mirrors.dotsrc.org/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# OSDN RebornOS Repository 2
Server = https://mirrors.tuna.tsinghua.edu.cn/osdn/storage/g/r/re/rebornos/repo/RebornOS/

# OSDN RebornOS Repository 3
Server = https://mirrors.xtom.com.hk/osdn//storage/g/r/re/rebornos/repo/RebornOS/

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

Save with <kbd>Ctrl</kbd> <kbd>O</kbd> and exit with <kbd>Ctrl</kbd> <kbd>X</kbd>.

