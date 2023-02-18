---
title: Pace
description: Pace is a GUI pacman.conf editor
published: true
date: 2023-02-18T17:15:36.571Z
tags: apps, pace, pacman.conf, repository
editor: markdown
dateCreated: 2023-02-18T16:52:45.879Z
---

# Install
Pace can be installed with the command
```
sudo pacman -S pace
```

# How to use Pace

Start Pace from your menu.

![](/apps/pacestartscreen.png)

You will see a list of repositories, the **slider** to the right means the repository is activated. You can enable and disable repositories by clicking on the **sliders**.

By using the plus button on the bottom right you can add custom repositories

![](/apps/customrepo.png)

Type the name of the repository you want to add and then click the plus this gives you a few options and by clicking the plus you can add  a total of 4 options 

-   **Server** 

Server = url

A full URL to a location where the database, packages, and signatures (if available) for this repository can be found.

During parsing, pacman will define the `$repo` variable to the name of the current section. This is often utilized in files specified using the *Include* directive so all repositories can use the same mirrorfile. pacman also defines the `$arch` variable to the first (or only) value of the `Architecture` option, so the same mirrorfile can even be used for different architectures.

-   **Include**  (here you can specify a configuration file for your repository)
 = /path/to/config/file

Include another configuration file. This file can include repositories or general configuration options. Wildcards in the specified paths will get expanded based on [_glob(7)_](https://archlinux.org/pacman/glob.7.html) rules.

-   **SigLevel**=
Set the signature verification level for this repository. For more information, see [_Package and Database Signature Checking_](https://archlinux.org/pacman/pacman.conf.5.html#SC) below

-   **Usage** Set the usage level for this repository. This option takes a list of tokens which must be at least one of the following:

**Sync**
Enables refreshes for this repository.

**Search**
Enables searching for this repository.

**Install**
Enables installation of packages from this repository during a `--sync` operation.

**Upgrade**
Allows this repository to be a valid source of packages when performing a `--sysupgrade`.

**All**
Enables all of the above features for the repository. This is the default if not specified.

Note that an enabled repository can be operated on explicitly, regardless of the Usage level set.

When you are done, click **Save**.

# Options
Here you can change various options for [pacman.conf](https://archlinux.org/pacman/pacman.conf.5.html) a list with explanation of all the options is available on the [man page](https://archlinux.org/pacman/pacman.conf.5.html), outside the scope of this guide.

![](/apps/paceoptions.png)

# Mirrorlist
Mirrorlist will show a list of all mirrors you have you can enable or disable them by clicking on the slider.

You can also delete them by clicking on the trashcan and modify them by clicking on the pen icon or add a new mirrors with the plus button.

It's not recommended to change settings here as mirrorlist get updated by Arch and RebornOS; however, if you want to update your mirrors, it's recommended.

To use [rate-mirrors](wiki.rebornos.org/en/apps/rate-mirrors) you can find a guide for it [here](wiki.rebornos.org/en/apps/rate-mirrors)

![](/apps/mirrorlist.png)

#  Saving changes
In order to save changes you made with any of the options from Pace, you need to click the preview button on the top left this will show all changes you made.
Now click save in the top right to save your changes.