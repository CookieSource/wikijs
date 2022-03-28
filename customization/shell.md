---
title: Shell
description: Guides on changing the look & feel of your terminal
published: true
date: 2022-03-28T12:16:17.042Z
tags: customization, themes, shell, zsh, fish, bash
editor: markdown
dateCreated: 2021-09-23T13:35:30.759Z
---

Here you can find a comparison of shell features compared to other shells.

# Bash

[Bash](https://gnu.org/software/bash) is the default Linux shell almost all distros use by default.

To install bash, run the command:

```
sudo pacman -S bash
```

## Set Bash as default shell

To list all installed shells, run:

```
chsh -l
```

And to set one as default for your user do:

```
chsh -s <full-path-to-shell>
```

If you are using [systemd-homed](https://wiki.archlinux.org/title/Systemd-homed), run: 

```
homectl update --shell=<full-path-to-shell> user
```

where *\<full-path-to-shell\>* is the full path as given by `chsh -l`.

If you now log out and log in again, you will be greeted by the other shell.
[**Oh My bash**](https://ohmybash.nntoan.com/)
# Zsh

[Zsh](https://zsh.org) is a shell similar to ksh with useful features of Bash, ksh, and tcsh and many original features.

To install zsh, run the command:

```plaintext
sudo pacman -S zsh
```

## Features

**Better tab completion**

In the context of the **cd** command this isn’t particularly useful, as you can only go into directories. Zsh knows this and only shows you the possible valid destinations.

![](https://code.joejag.com/assets/2014/cd_after.jpg)

**Better history searcher**

You may be familiar with using **+R** for performing a recursive search to find a previous command you typed in. This is a great way to reuse commands in Bash and Zsh.

Zsh goes one better. You can type part of a command and press

![](https://code.joejag.com/assets/2014/history_before.jpg)

It finds the last command we typed starting with ‘ls’. We could continue pressing up to cycle if we wanted.

![](https://code.joejag.com/assets/2014/history_after.jpg)

[**Oh my Zsh**](https://ohmyz.sh/) is a community-driven framework for managing your Zsh configuration to improve it with themes and plugins for extra functionality.

## Set Zsh as default shell

To list all installed shells, run:

```plaintext
chsh -l
```

And to set one as default for your user do:

```plaintext
chsh -s <full-path-to-shell>
```

If you are using [systemd-homed](https://wiki.archlinux.org/title/Systemd-homed), run: 

```plaintext
homectl update --shell=<full-path-to-shell> user
```

where *\<full-path-to-shell\>* is the full path as given by `chsh -l`.

If you now log out and log in again, you will be greeted by the other shell.

# Fish

[fish](https://fishshell.com/) - the friendly interactive shell is a shell that focuses on usability. It is compatible with bash, and has its own syntax. It has various unique features too.

To install fish, run the command:

```
sudo pacman -s fish
```

## Features

Fish has multiple features that makes it stand out from bash out of the box such as:

**Autosuggestions**  
Autosuggestion suggests commands as you type based on history and completion, like many web browsers.

![Autosuggestion Thumbnail](https://fishshell.com/assets/img/screenshots/autosuggestion_thumb.png)

**Web Based Configuration**

You can set your colors, view functions, variables, and history all from a web page.

![Web Config Thumbnail](https://fishshell.com/assets/img/screenshots/web_config_thumb.png)

**Works Out of the Box**

Fish has features like tab completions and syntax highlighting, with nothing new to learn or configure.

![Works Out of the Box Thumbnail](https://fishshell.com/assets/img/screenshots/works_out_of_the_box_thumb.png)

[**Oh my Fish**](https://github.com/oh-my-fish/oh-my-fish) provides core infrastructure to allow you to install packages which extend or modify the look of your shell. It's fast, extensible and easy to use.

## Set Fish as default shell

To list all installed shells, run:

```
chsh -l
```

And to set one as default for your user do:

```
chsh -s <full-path-to-shell>
```

If you are using [systemd-homed](https://wiki.archlinux.org/title/Systemd-homed), run: 

```
homectl update --shell=<full-path-to-shell> user
```

where *\<full-path-to-shell\>* is the full path as given by `chsh -l`.

If you now log out and log in again, you will be greeted by the other shell.