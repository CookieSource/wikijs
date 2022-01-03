---
title: How to configure jackett in qbittorrent
description: jackett-in-qbittorrent
published: true
date: 2021-09-24T00:14:22.940Z
tags: jackett qbittorrent
editor: markdown
dateCreated: 2021-09-24T00:14:19.854Z
---

# How to configure jackett in qbittorrent

jackett (jackett-bin in RebornOS) will allow qbittorrent to use more file search options. Let's see how to configure it.


Open qbittorrent:

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/how-to-use-jackett-in-qbittorrent/-/raw/main/qbittorent-main.png">
</p>

Go to: View --> click in ***Search Engine***
Access the tab marked ***Search***:

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/how-to-use-jackett-in-qbittorrent/-/raw/main/qbittorrent-search-plugins.png">
</p>

Click on the button ***Search plugins ...***:

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/how-to-use-jackett-in-qbittorrent/-/raw/main/qbittorrent-plugins.png">
</p>

Click in ***Check for updates***

When the update installation is complete, click ***OK***, and click ***Close***.

Close qbittorrent.

Now, install jackett-bin:

```
sudo pacman -S jackett-bin
```

Activate the service:

```
sudo systemctl enable --now jackett.service
```

Then, from your web browser, access the jackett page:

```
http://127.0.0.1:9117/UI/Dashboard
```

You will see a page like the one below:

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/how-to-use-jackett-in-qbittorrent/-/raw/main/jackett-0001.png">
</p>

Here, click in ***+ Add indexer***:

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/how-to-use-jackett-in-qbittorrent/-/raw/main/jackett-0002.png">
</p>


Suppose we want to add the indexes of the public sites (all or some of them). So in the ***Search*** field, let's type pub. We will see a page like the one below:

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/how-to-use-jackett-in-qbittorrent/-/raw/main/jackett-0003.png">
</p>


Select one, several, or all of the items, and then at the end, click on ***Add Selected***.

**NOTE**: The addition of the indexes will take more time, according to the number of them that have been selected. The more indexes you select, the longer it will take to add them. So be patient.

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/how-to-use-jackett-in-qbittorrent/-/raw/main/jackett-select.png">
</p>

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/how-to-use-jackett-in-qbittorrent/-/raw/main/Add_Selected_and_Close.png">
</p>

Now to add these indexes in qbittorrent, we will have to edit the following file (***without using sudo***):

```
nano ~/.local/share/qBittorrent/nova3/engines/jackett.json
```

Content:

```
{
    "api_key": "YOUR_API_KEY_HERE", 
    "tracker_first": false, 
    "url": "http://127.0.0.1:9117"
}
```

From Jackett page, copy the ***API Key*** value here:

<p align="center">
<img src="https://gitlab.com/rebornos-team/rebornos-images-for-wiki/how-to-use-jackett-in-qbittorrent/-/raw/main/API_Key.png">
</p>

Copy te API key:

```
{
    "api_key": "mynjt47fzbhjw5u3jzf4tcczc3555i72", 
    "tracker_first": false, 
    "url": "http://127.0.0.1:9117"
}
```

Save (***Ctrl+o***) and exit (***Ctrl+x***).

Ready.

Now when you open qbittorrent and search for something, more results will be presented.
