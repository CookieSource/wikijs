---
title: KDE Partition Manager
description: KDE Partition Manager is a utility program to help you manage the disk devices, partitions and file systems on your computer. It allows you to easily create, copy, move, delete, resize without losing data, backup and restore partitions.
published: true
date: 2022-04-07T11:48:03.651Z
tags: 
editor: markdown
dateCreated: 2021-09-29T12:07:55.870Z
---

# Installing KDE Partition Manager

To install KDE Partition Manager, run

```plaintext
sudo pacman -S partitionmanager
```

# How to use KDE Partition Manager

Start the partition manager from your menu

When you open the partition manager, you will be greeted with a prompt asking you to authenticate your identity. Input your password and press enter. The partition manager will then start scanning your disk so that it has a record of all the disk devices present in your system.

![](https://linuxhint.com/wp-content/uploads/2020/09/word-image-494.png)

![](https://linuxhint.com/wp-content/uploads/2020/09/word-image-495.png)

After scanning, the app will then present you with a complete outline of your disk drives, giving details including the type of partition, the total size of the partition, the amount of space used up, and so on. The main components of the KDE Partition Manager include the **devices** panel, which lists all the devices that can be found on your system; the **graphical** and **tree view**, which both show a different representation of the partitions; **pending operations**,which contain all the operations waiting to be executed; and a few other panels.

![](https://linuxhint.com/wp-content/uploads/2020/09/word-image-496.png)

You can add more panels by going to the **Settings** menu item and then checking the panels you want to appear in the **Panels Shown** section.

To resize or delete any partition, first, select the correct device from the devices panel and then right-click on the partition to which you would like to apply the desired action. Click **unmount**. This is done because you can only apply actions to an unmounted partition.

![](https://linuxhint.com/wp-content/uploads/2020/09/word-image-497.png)

To resize the partition, either once again right-click and select the **resize/move** option or hit the keys **Ctrl + R**, which will open the following dialog:

![](https://linuxhint.com/wp-content/uploads/2020/09/word-image-498.png)

You can play around with the memory size. Once you are satisfied with the values, press **OK**, which will add a new operation to the pending operations list, along with updating the graphical and tree views.

![](https://linuxhint.com/wp-content/uploads/2020/09/word-image-54.jpeg)

After resizing and applying the other corresponding actions, you need to apply these changes to make them permanent. This can be done by going to the **Edit** menu item and selecting **Apply**. This will open a dialog box to confirm whether you want to apply all the pending operations. Click **OK** and the process will start. Once all pending operations have been applied, you will receive a success message, along with a report containing all the details of the entire process.

![](https://linuxhint.com/wp-content/uploads/2020/09/word-image-499.png)

KDE Partition Manager can also be used to **format** your partitions. To do this, once again, **unmount** your partition, and press the <kbd>delete</kbd> button or right-click and select the **delete** option, after which your partition should look something like this:

![](https://linuxhint.com/wp-content/uploads/2020/09/word-image-500.png)

Next, right-click and select the **New** option or <kbd>Ctrl</kbd> <kbd>N</kbd>, which will open the following prompt:

![](https://linuxhint.com/wp-content/uploads/2020/09/word-image-501.png)

![](https://linuxhint.com/wp-content/uploads/2020/09/word-image-502.png)

Set the options that you want your partition to have and then hit **OK** (be sure to select what type of **file system** you want your new partition to be). The following image shows the result that you should get after performing this action:

Now, click the **Apply** button from the **Edit** menu item, click **OK** on the pending operations dialog, and then wait till the process finishes, after which you will see something like this:

![](https://linuxhint.com/wp-content/uploads/2020/09/word-image-503.png)