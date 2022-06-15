---
title: How to generate thumbnails for videos in Xfce
description: 
published: true
date: 2022-03-21T11:57:28.591Z
tags: xfce
editor: markdown
dateCreated: 2021-09-25T15:36:48.380Z
---

# How to generate thumbnails for videos in Xfce

For this procedure to work, [**Tumbler**](https://archlinux.org/packages/extra/x86_64/tumbler/) must be installed. It can be installed with
```
sudo pacman -S tumbler
```

**(1).** Create the folder named `tumbler` inside the existing `.config` folder in the home directory (**NOTE:** **DO NOT** use sudo):

```
mkdir ~/.config/tumbler
```

**(2).** Copy the tumbler configuration file into the config folder (**NOTE:** **DO NOT** use sudo):

```
cp /etc/xdg/tumbler/tumbler.rc ~/.config/tumbler/
```

**(3).** Edit the file (**NOTE:** **DO NOT** use sudo):

```
nano ~/.config/tumbler/tumbler.rc
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

**(5).** Under `# ffmpegthumbnailer plugin`, change the `MaxFileSize` value from **214748364** to **0**:

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

**(6).** Save (<kbd>Control</kbd> <kbd>O</kbd>), and exit (<kbd>Control</kbd> <kbd>X</kbd>). Restart the system. Ready.