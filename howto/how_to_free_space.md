---
title: How to free space
description: In this how to you are going to learn how to free up some storage.
published: true
date: 2022-08-21T11:23:47.631Z
tags: 
editor: markdown
dateCreated: 2021-12-27T21:33:42.145Z
---

# Cleaning package cache

`pacman`, the package manager for RebornOS keeps packages in cache so if they need to be reinstalled its quick and easy but sometimes they tend to collect some big packages that are mostly not needed they are stored in `/var/cache/pacman/pkg/` you can see how big the cache is by running `du -sh /var/cache/pacman/pkg/`. There are two ways of reclaiming that space **Manually** or **Automatically**.

One option is to remove cached packages that are not currently installed:

```
sudo pacman -Sc
```

Another way to clean the `/var/cache/pacman/pkg/` directory is to **use a script** that automatically deletes all cached versions of installed and uninstalled packages, except for the most recent 3 versions. The script is called `paccache`. You can install it with the [`pacman-contrib`](https://archlinux.org/packages/community/x86_64/pacman-contrib) package - 

```
sudo pacman -S pacman-contrib
```

You can run `paccache` every time after you run `pacman`. So, you need to [create a Hook](https://wiki.archlinux.org/title/Pacman#Hooks) for that. Just create a file `/usr/share/libalpm/hooks/paccache.hook`.

```
sudo nano /usr/share/libalpm/hooks/paccache.hook
```

Add this content into the file, then press <kbd>Control</kbd> <kbd>S</kbd> and <kbd>Control</kbd> <kbd>X</kbd>

```ini
[Trigger]
Operation = Upgrade
Operation = Install
Operation = Remove
Type = Package
Target = *

[Action]
Description = Cleaning pacman cache with paccache …
When = PostTransaction
Exec = /usr/bin/paccache -r
```
# Clean old log files
Every Linux distribution has a logging mechanism that help you investigate what’s going on your system. You’ll have kernel logging data, system log messages, standard output and errors for various services in RebornOS. The problem is that over the time, these logs take a considerable amount of disk space. You can check the log size with this command:
```
journalctl --disk-usage
```


Now, there are ways to clean systemd journal logs. The easiest for you is to clear the logs that are older than a certain days.
```
sudo journalctl --vacuum-time=3d
```
# Use BleachBit
Learn how to use BleachBit [here](/apps/bleachbit)

# Clean the cache in your home folder

As we use our system, the cache will fill up and take up a lot of space. So, the first thing you probably would want to do is to clean cache in your user directory. If you want to check the size of your cache folder you can do it with this command:

```
sudo du -sh ~/.cache/
```

To clean it you need to remove all files inside it:

```
rm -rf ~/.cache/*
```

And that is it.

# Find the largest files and directories

You can check what the largest files in your system are and maybe you do not need them. To accomplish this task, you can use some command line tools or graphical programs.

If you are using **GNOME** you can use [`baobab`](https://archlinux.org/packages/extra/x86_64/baobab). There are some other tools listed on the [Arch Wiki](https://wiki.archlinux.org/title/List_of_applications/Utilities#Disk_usage_display):

> ##### Console
> 
> -   **duc** — A library and suite of tools for inspecting disk usage.
> 
> [https://duc.zevv.nl/](https://duc.zevv.nl/) || [duc](https://aur.archlinux.org/packages/duc/)^AUR^
> 
> -   **gdu** — Disk usage analyzer with console interface written in Go.
> 
> [https://github.com/Dundee/gdu](https://github.com/Dundee/gdu) || [gdu](https://aur.archlinux.org/packages/gdu/)^AUR^
> 
> -   **gt5** — Diff-capable "du-browser".
> 
> [http://gt5.sourceforge.net](http://gt5.sourceforge.net) || [gt5](https://aur.archlinux.org/packages/gt5/)^AUR^
> 
> -   **ncdu** — Simple ncurses disk usage analyzer.
> 
> [https://dev.yorhel.nl/ncdu](https://dev.yorhel.nl/ncdu) || [ncdu](https://archlinux.org/packages/?name=ncdu)
> 
> ##### Graphical
> 
> -   [**Filelight**](https://en.wikipedia.org/wiki/Filelight) — Disk usage analyzer that creates an interactive map of concentric, segmented rings that help visualise disk usage on your computer.
> 
> [https://apps.kde.org/filelight/](https://apps.kde.org/filelight/) || [filelight](https://archlinux.org/packages/?name=filelight)
> 
> -   [**GNOME Disk Usage Analyzer**](https://en.wikipedia.org/wiki/Disk_Usage_Analyzer) — Disk usage analyzer for the [GNOME](https://wiki.archlinux.org/title/GNOME) desktop to check folder sizes and available disk space.
> 
> [https://wiki.gnome.org/Apps/DiskUsageAnalyzer](https://wiki.gnome.org/Apps/DiskUsageAnalyzer) || [baobab](https://archlinux.org/packages/?name=baobab)
> 
> -   **Graphical Disk Map** — Disk usage analyzer that draws a map of rectangles sized according to file or dir sizes.
> 
> [http://gdmap.sourceforge.net/](http://gdmap.sourceforge.net/) || [gdmap](https://archlinux.org/packages/?name=gdmap)
> 
> -   **fsview (part of Konqueror)** — KDE based disk usage analyzer that draws a map of rectangles sized according to file or dir sizes.
> 
> [https://docs.kde.org/trunk5/en/konqueror/konqueror/view-extensions.html](https://docs.kde.org/trunk5/en/konqueror/konqueror/view-extensions.html) || [konqueror](https://archlinux.org/packages/?name=konqueror)
> 
> -   **MATE Disk Usage Analyzer** — Disk usage analyzing tool for MATE Desktop.
> 
> [https://github.com/mate-desktop/mate-utils](https://github.com/mate-desktop/mate-utils) || [mate-utils](https://archlinux.org/packages/?name=mate-utils)
> 
> -   **qdirstat** — Qt-based directory statistics (KDirStat/K4DirStat without any KDE - from the original KDirStat author).
> 
> [https://github.com/shundhammer/qdirstat](https://github.com/shundhammer/qdirstat) || [qdirstat](https://aur.archlinux.org/packages/qdirstat/)^AUR^