---
title: How to use Zram instead of Zswap
description: 
published: true
date: 2022-10-24T21:36:32.722Z
tags: zswap zram swap
editor: markdown
dateCreated: 2022-10-14T04:19:39.265Z
---

There is much information about configuring Zram, but some might be a little confusing, especially for someone who hasn't been using Linux and it can be challenging to say the least. I also realized Zram and Zwap is already included with the kernel, so there is no need to install any additional package.  I found a few guides and picked one and followed the instructions. Even when following instruction steps, you can still have some things that might not go well.  This is what happened, I followed the guidance of Daniel Wayne Armstrong's [blog]( https://www.dwarmstrong.org/zram-swap/), but found I had to tweak or adjust it so that it would work. For some experienced Linux users, they might not have any troubles and I'm sure there's other methods that will also work, but this is what I did and i'm just sharing my experience and setup.

I had some trouble in the beginning, partly because I didn't understand some of the requirements and also ensuring the default Zswap wasn't being used. If Zswap is used, the kernel will use it first before using Zram. Also, I read that you should have a Zram swap that's about 20% (percent) of the actual system RAM, but you can also create several of these to allow for better handling of swap needed by the system. To quote kernel.org,
> Note: There is little point creating a zram of greater than twice the size of memory since we expect a 2:1 compression ratio. Note that zram uses about 0.1% of the size of the disk when not in use so a huge zram is wasteful.

Once I stopped Zswap, I still saw it was present, but believe is due to it being embedded in the kernel, so I just ignored it, and used the zwap.enabled=0 in the kernel parameters and added it via editing /etc/default/grub, as per the guidance in the Arch Wiki on Zswap. Also, you can always go back to using Zswap just by taking out the kernel parameter from grub.

Here is where to add the kernel parameter to not allow Zswap to start (which is default ‘on’ in the current kernel).  Pick your favorite editor (for example nano),

`sudo nano /etc/default/grub`

and add the following line:
```
GRUB_CMDLINE_LINUX_DEFAULT="zswap.enabled=0"
```

To make the parameter updated in grub, run:

`sudo grub-mkconfig -o /boot/grub/grub.cfg`  
  
This can also be toggled off with the command, and will need to do this if you didn't already toggle it in the kernel parameters and turn off any swaps:  

`sudo swapoff --all`
`sudo bash -c "echo 0 > /sys/module/zswap/parameters/enabled"`

Here we see that zswap is not enabled. 

```
$ cat /sys/module/zswap/parameters/enabled`
N
```
Here you can still the zswap process, but they are not running as time is 00:00:00.

```
$ ps -ef | grep zswap 
root         121       2  0 Oct11 ?        00:00:00 [zswap1] 
root         122       2  0 Oct11 ?        00:00:00 [zswap1] 
root         123       2  0 Oct11 ?        00:00:00 [zswap-shrink]
```

After disabling zswap in the kernel parameter you can see that it was executed at boot.

```
$ cat /proc/cmdline  
BOOT_IMAGE=/boot/vmlinuz-linux root=UUID=2b4f9d37-c068-45f8-a663-ef34758944f6 rw zswap.enabled=0
```

Next, I made sure that the Zram configurations were correctly added as per the steps in the guide.

I would check each file after doing the steps to configure Zram, to ensure no typo or encounter some error during the steps.

1.Enable the zram kernel module and optionally define the number of devices. 

`sudo modprobe zram num_devices=1`

2. Check for, then select the compression algorithm for the zram disk(s).

`cat /sys/block/zram0/comp_algorithm`

`sudo bash -c “echo zstd > /sys/block/zram0/comp_algorithm”`

3. Set the size of the Zram disk.  You should definitely check this after setting to ensure the correct value is present.

`sudo bash -c “echo 3G > /sys/block/zram0/disksize”`  

This is after executing the commands to select the compression algorithm & define the size of the zram0 disk (mine is using zstd and 3GB). 

```plaintext
$ cat /sys/block/zram0/comp_algorithm 
lzo lzo-rle lz4 lz4hc 842 [zstd] 
$ cat /sys/block/zram0/disksize 
3221225472
```

4.  Create and start the zram swap with highest priority.  Check it all went well.  I would switch to root account and redo it if the zram or parameters did not seem to take.

```plaintext
$ sudo mkswap --label zram0 /dev/zram0
$ sudo swapon --priority 32767 /dev/zram0
$ zramctl 
NAME       ALGORITHM DISKSIZE  DATA  COMPR  TOTAL STREAMS MOUNTPOINT 
/dev/zram0 zstd            3G  1.2G 154.7M 269.2M       8 [SWAP]
```

5. If it all checks out and it's how you wanted it setup, then create the service and enable it and add the zram\_*start and zram\_*stop scripts to /usr/local/bin/ and set the execute bit on them (chmod +x).  The scripts will contain the commands to re-create and re-enable the zram as well as stop the zram and reset it.  Here's what mine contain and I use vim, you can use whatever editor or method you are comfortable with:

`sudo vim /usr/local/bin/zram_start`

```plaintext
#!/bin/bash
# Select the compression algorithm
echo zstd > /sys/block/zram0/comp_algorithm
# Create the zram0 swap for 3GB size
echo 3G  > /sys/block/zram0/disksize
# Enable the zram0 with highest priority
mkswap --label zram0 /dev/zram0
swapon --priority 32767 /dev/zram0
```

`sudo vim /usr/local/bin/zram_stop`

```plaintext
#!/bin/bash
#Disable swap
swapoff /dev/zram0
# Reset the zram0 flushing it
echo 1 > /sys/block/zram0/reset
```

`sudo chmod +x /usr/local/bin/zram_st*`

`sudo vim /etc/systemd/system/zram-swap.service`

```ini
[Unit] 
Description=Configure zram swap device 
After=local-fs.target 

[Service] 
Type=oneshot 
ExecStart=/usr/local/bin/zram_start 
ExecStop=/usr/local/bin/zram_stop 
RemainAfterExit=yes 

[Install] 
WantedBy=multi-user.target
```

`sudo systemctl enable zram-swap`

To check the status of the zram-swap, make sure there's no error or incorrect setting.

`sudo systemctl status zram-swap`

6. Tuning the performance, I just used the same recommendations given by D.W. Armstrong.

`sudo vim /etc/sysctl.d/99-sysctl.conf`

```plaintext
vm.vfs_cache_pressure=500 
vm.swappiness=100 
vm.dirty_background_ratio=1 
vm.dirty_ratio=50
```

Repeat steps 2 through 4 for any additional zram disks, be sure to add them to the start and stop scripts as well.  With all this done, now you should have a high performance zram swap that's ready to go the next time the system is restarted.

#### Reference links:

https://www.dwarmstrong.org/zram-swap/

https://docs.kernel.org/admin-guide/blockdev/zram.html

https://linuxreviews.org/zram

https://wiki.archlinux.org/title/Improving\_performance#zram\_or\_zswap

https://wiki.archlinux.org/title/Sysctl#Virtual\_memory