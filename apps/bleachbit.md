---
title: BleachBit
description: Bleachbit System cleaner
published: true
date: 2023-02-18T17:08:31.385Z
tags: apps, bleachbit, cleaner
editor: markdown
dateCreated: 2023-02-18T16:52:17.241Z
---

# Install
To install BleachBit, run
```
sudo pacman -S bleachbit
```

# Use BleachBit
Launch the BleachBit system cleaner from the app menu, you will get the default interface looks like below.  It will popup with preference window and you can customize what you want.

![](https://2daygeek.com/wp-content/uploads/2016/01/install-bleachbit-system-cleaner-in-linux-1.png)
See the BleachBit system cleaner interface.
![](https://2daygeek.com/wp-content/uploads/2016/01/install-bleachbit-system-cleaner-in-linux-2.png)

Choose all the options to clean everything. When you choose **Deep Scan**, **Firefox**, or **System**, it will popup below warning messages. - **Deep Scan** will make this process bit slow due to clearing following files such as Backup files, `.DS_Store`, `Thumbs.db`, and other temporary files
- **Firefox** option will warn you about deleting your saved passwords. 
- **System** also will make this process bit slow due to deep analysis of following options such as Free disk space, Localizations, and Memory.
![](https://2daygeek.com/wp-content/uploads/2016/01/install-bleachbit-system-cleaner-in-linux-3.png)
Hit `Preview` button to show junk files and how much storage they use. 
![](https://2daygeek.com/wp-content/uploads/2016/01/install-bleachbit-system-cleaner-in-linux-5b.png)

Hit **Clean** button to start clearing the unwanted junk files and caches. It will ask your confirmation, before initiate a process (select **Delete** button). When you run the app as a normal user, you will get lot of error messages while cleaning **System**. 

![](https://2daygeek.com/wp-content/uploads/2016/01/install-bleachbit-system-cleaner-in-linux-4.png)

Cleaning junk files under progress:

![](https://2daygeek.com/wp-content/uploads/2016/01/install-bleachbit-system-cleaner-in-linux-5a.png)

Cleaning has been done and now shows statistics about, how much disk space to be recovered and how many files get deleted in this activity.

![](https://2daygeek.com/wp-content/uploads/2016/01/install-bleachbit-system-cleaner-in-linux-6a.png)

For deep cleaning, including system junk files run BleachBit with `sudo` privilege:
```
sudo bleachbit
```
Then, follow the above steps after launching the bleachbit to clean junk files.
![](https://2daygeek.com/wp-content/uploads/2016/01/install-bleachbit-system-cleaner-in-linux-6.png)