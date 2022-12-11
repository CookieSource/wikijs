---
title: BleachBit
description: Bleachbit System cleaner
published: true
date: 2022-12-11T05:11:55.881Z
tags: apps, bleachbit, cleaner
editor: markdown
dateCreated: 2021-09-28T09:33:48.599Z
---

# How to install BleachBit

To install BleachBit, run

```plaintext
sudo pacman -S bleachbit
```

# How to use BleachBit?

Launch the BleachBit system cleaner from the app menu, you will get the default interface looks like below. 

It will popup with preference window and you can customize what you want.

![](https://2daygeek.com/wp-content/uploads/2016/01/install-bleachbit-system-cleaner-in-linux-1.png)

See the BleachBit system cleaner interface.

![](https://2daygeek.com/wp-content/uploads/2016/01/install-bleachbit-system-cleaner-in-linux-2.png)

Choose all the options to clean everything. When you choose Deep Scan, Firefox, & system will popup below warning messages.

-   Deep Scan will make this process bit slow due to clearing following files such as Backup files, `.DS_Store`, `Thumbs.db`, and Temporary files
-   Firefox option will warn you about deleting your saved passwords.
-   System also will make this process bit slow due to deep analysis of following options such as Free disk space, Localizations, and Memory.

![](https://2daygeek.com/wp-content/uploads/2016/01/install-bleachbit-system-cleaner-in-linux-3.png)

Hit `Preview` button to show junk files and how much storage they use.

![](https://2daygeek.com/wp-content/uploads/2016/01/install-bleachbit-system-cleaner-in-linux-5b.png)

Hit `Clean` button to start clearing the unwanted junk files and caches. It will ask your confirmation, before initiate a process (select `Delete` button). When you run the bleachbit as a normal user, you will get lot of error messages while cleaning `system` parameter

![](https://2daygeek.com/wp-content/uploads/2016/01/install-bleachbit-system-cleaner-in-linux-4.png)

Cleaning junk files under progress.

![](https://2daygeek.com/wp-content/uploads/2016/01/install-bleachbit-system-cleaner-in-linux-5a.png)

cleaning has been done and finally showing statistic about, how much disk space to be recovered and how many files get deleted in this activity.

![](https://2daygeek.com/wp-content/uploads/2016/01/install-bleachbit-system-cleaner-in-linux-6a.png)

For deep cleaning, including system junk files run bleachbit with `sudo` privilege.

```plaintext
sudo bleachbit
```

Follow the above steps after launching the bleachbit to clean junk files.

![](https://2daygeek.com/wp-content/uploads/2016/01/install-bleachbit-system-cleaner-in-linux-6.png)