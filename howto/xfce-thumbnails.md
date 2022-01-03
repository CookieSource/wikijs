---
title: How to generate thumbnails for videos in XFCE
description: XFCE thumbnails
published: true
date: 2021-09-26T13:39:26.338Z
tags: xfce
editor: markdown
dateCreated: 2021-09-25T15:36:48.380Z
---

# How to generate thumbnails for videos in XFCE

For this procedure to work, **tumbler** must be installed. The installation made through RebornOS meets this requirement:

```
sudo pacman -S tumbler
```

**(1).** Create the folder named **tumbler** inside the existing **.config** folder in the user's directory (**NOTE:** **DO NOT** use sudo):

```
mkdir $HOME/.config/tumbler
```

**(2).** Copy the tumbler configuration file into this folder (**NOTE:** **DO NOT** use sudo):

```
cp /etc/xdg/tumbler/tumbler.rc $HOME/.config/tumbler/
```

**(3).** Edit the file (**NOTE:** **DO NOT** use sudo):

```
nano $HOME/.config/tumbler/tumbler.rc
```

**(4).** Search for:

```
###
# Video Thumbnailers
###

# Download cover from omdbapi.com or themoviedb.org if an
# API key is given. This plugin is disabled because it
# sends your (private) movie names over the internet.
[CoverThumbnailer]
Disabled=true
Priority=3
Locations=~/movies
MaxFileSize=0
#APIKey=your-api-key-from-themoviedb.org

# ffmpegthumbnailer plugin
[FfmpegThumbnailer]
Disabled=false
Priority=2
Locations=
MaxFileSize=2147483648
```

**(5).** Under **# ffmpegthumbnailer plugin**, change the **MaxFileSize** value from **214748364** to **0**:

```
###
# Video Thumbnailers
###

# Download cover from omdbapi.com or themoviedb.org if an
# API key is given. This plugin is disabled because it
# sends your (private) movie names over the internet.
[CoverThumbnailer]
Disabled=true
Priority=3
Locations=~/movies
MaxFileSize=0
#APIKey=your-api-key-from-themoviedb.org

# ffmpegthumbnailer plugin
[FfmpegThumbnailer]
Disabled=false
Priority=2
Locations=
MaxFileSize=0
```

**(6).** Save (**Ctrl+o**), and exit (**Ctlr+x**). Restart the system. Ready.


