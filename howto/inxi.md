---
title: How to use inxi
description: inxi
published: true
date: 2023-02-18T17:05:39.896Z
tags: inxi
editor: markdown
dateCreated: 2023-02-18T16:56:08.954Z
---

# How to use inxi

**NOTE:** inxi is installed by default on RebornOS. inxi run from the terminal.

inxi options:

```
$ inxi --help
inxi supports the following options. For more detailed information, see man inxi. If you start inxi with no arguments, it will 
display a short system summary. 

You can use these options alone or together, to show or add the item(s) you want to see: A, B, C, D, E, G, I, J, L, M, N, P, R, 
S, W, d, f, i, j, l, m, n, o, p, r, s, t, u, w, --slots. If you use them with -v [level], -b or -F, inxi will add the requested 
lines to the output. 

Examples: inxi -v4 -c6 OR inxi -bDc 6 OR inxi -FzjJxy 80
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
Output Control Options (see Extra Data Options to extend output):
 -A, --audio          Audio/sound devices(s), driver, running sound servers.
 -b, --basic          Basic output, short form. Same as inxi -v 2.
 -B, --battery        System battery info, including charge, condition voltage (if critical), plus extra info (if battery 
                      present/detected). 
 -c, --color          Set color scheme (0-42). For piped or redirected output, you must use an explicit color selector. 
                      Example: inxi -c 11 
                      Color selectors let you set the config file value for the selection (NOTE: IRC and global only show safe 
                      color set) 
                         94  Console, out of X
                         95  Terminal, running in X - like xTerm
                         96  Gui IRC, running in X - like Xchat, Quassel, Konversation etc.
                         97  Console IRC running in X - like irssi in xTerm
                         98  Console IRC not in X
                         99  Global - Overrides/removes all settings. Setting specific removes global.
 -C, --cpu            CPU output, including per CPU clock speed and max CPU speed (if available).
 -d, --disk-full, --optical
                      Optical drive data (and floppy disks, if present). Triggers -D.
 -D, --disk           Hard Disk info, including total storage and details for each disk. Disk total used percentage includes 
                      swap partition size(s). 
 -E, --bluetooth      Show bluetooth device data and report, if available. Shows state, address, IDs, version info.
 -f, --flags          All CPU flags. Triggers -C. Not shown with -F to avoid spamming.
 -F, --full           Full output. Includes all Upper Case line letters (except -J, -W) plus --swap, -s and -n. Does not show 
                      extra verbose options such as -d -f -i -J -l -m -o -p -r -t -u -x, unless specified. 
 -G, --graphics       Graphics info (devices(s), drivers, display protocol (if available), display server/Wayland compositor, 
                      resolution, renderer, OpenGL version). 
 -i, --ip             WAN IP address and local interfaces (requires ifconfig or ip network tool). Triggers -n. Not shown with 
                      -F for user security reasons. You shouldn't paste your local/WAN IP. 
 -I, --info           General info, including processes, uptime, memory, IRC client or shell type, inxi version.
 -j, --swap           Swap in use. Includes partitions, zram, file.
 -J, --usb            Show USB data: Hubs and Devices.
 -l, --label          Partition labels. Triggers -P. For full -p output, use -pl.
 -L, --logical        Logical devices, LVM (VG, LV), LUKS, Crypto, bcache, etc. Shows components/devices, sizes, etc.
 -m, --memory         Memory (RAM) data. Requires root. Numbers of devices (slots) supported and individual memory devices 
                      (sticks of memory etc). For devices, shows device locator, size, speed, type (e.g. DDR3). If neither -I 
                      nor -tm are selected, also shows RAM used/total. 
     --memory-modules Memory (RAM) data. Exclude empty module slots.
     --memory-short   Memory (RAM) data. Show only short Memory RAM report, number of arrays, slots, modules, and RAM type.
 -M, --machine        Machine data. Device type (desktop, server, laptop, VM etc.), motherboard, BIOS and, if present, system 
                      builder (e.g. Lenovo). Shows UEFI/BIOS/UEFI [Legacy]. Older systems/kernels without the required /sys 
                      data can use dmidecode instead, run as root. Dmidecode can be forced with --dmidecode 
 -n, --network-advanced
                      Advanced Network device info. Triggers -N. Shows interface, speed, MAC id, state, etc. 
 -N, --network        Network device(s), driver.
 -o, --unmounted      Unmounted partition info (includes UUID and Label if available). Shows file system type if you have lsblk 
                      installed (Linux) or, for BSD/GNU Linux, if 'file' installed and you are root or if you have added to 
                      /etc/sudoers (sudo v. 1.7 or newer)(BSDs: see doas). 
                      Example:  <username> ALL = NOPASSWD: /usr/bin/file 
 -p, --partitions-full
                      Full partition information (-P plus all other detected partitions).
 -P, --partitions     Basic partition info. Shows, if detected: / /boot /home /opt /tmp /usr /usr/home /var /var/log /var/tmp. 
                      Swap partitions show if --swap is not used. Use -p to see all mounted partitions. 
 -r, --repos          Distro repository data. Supported repo types: APK, APT, CARDS, EOPKG, NIX, PACMAN, PACMAN-G2, PISI, PKG 
                      (BSDs), PORTAGE, PORTS (BSDs), SCRATCHPKG, SLACKPKG, TCE, URPMQ, XBPS, YUM/ZYPP. 
 -R, --raid           RAID data. Shows RAID devices, states, levels, array sizes, and components. md-raid: If device is 
                      resyncing, also shows resync progress line. 
 -s, --sensors        Sensors output (if sensors installed/configured): mobo/CPU/GPU temp; detected fan speeds. GPU temp only 
                      for Fglrx/Nvidia drivers. Nvidia shows screen number for > 1 screen. IPMI sensors if present. 
     --slots          PCI slots: type, speed, status. Requires root.
 -S, --system         System info: host name, kernel, desktop environment (if in X/Wayland), distro.
 -t, --processes      Processes. Requires extra options: c (CPU), m (memory), cm (CPU+memory). If followed by numbers 1-x, 
                      shows that number of processes for each type (default: 5; if in IRC, max: 5). 
                      Make sure that there is no space between letters and numbers (e.g. -t cm10).
 -u, --uuid           Partition UUIDs. Triggers -P. For full -p output, use -pu.
 -v, --verbosity      Set inxi verbosity level (0-8). Should not be used with -b or -F. Example: inxi -v 4
                          0  Same as: inxi
                          1  Basic verbose, -S + basic CPU + -G + basic Disk + -I.
                          2  Networking device (-N), Machine (-M), Battery (-B; if present), and, if present, basic RAID 
                             (devices only; notes if inactive). Same as inxi -b 
                          3  Advanced CPU (-C), battery (-B), network (-n); triggers -x. 
                          4  Partition size/used data (-P) for (if present) /, /home, /var/, /boot. Shows full disk data (-D). 
                          5  Audio device (-A), sensors (-s), memory/RAM (-m), bluetooth (if present), partition label (-l), 
                             full swap (-j), UUID (-u), short form of optical drives, RAID data (if present). 
                          6  Full partition (-p), unmounted partition (-o), optical drive (-d), USB (-J), full RAID; triggers 
                             -xx. 
                          7  Network IP data (-i), bluetooth, logical (-L), RAID forced; triggers -xxx.
                          8  Everything available, including repos (-r), processes (-tcm), PCI slots (--slots); triggers admin 
                             (-a). 
 -w, --weather        Local weather data/time. To check an alternate location, see -W. NO AUTOMATED QUERIES ALLOWED!
 -W, --weather-location
                      [location] Supported options for [location]: postal code[,country/country code]; city, state 
                      (USA)/country (country/two character country code); latitude, longitude. Only use if you want the weather 
                      somewhere other than the machine running inxi. Use only ASCII characters, replace spaces in 
                      city/state/country names with '+'. Example: inxi -W [new+york,ny london,gb madrid,es] 
     --weather-source [1-9] Change weather data source. 1-4 generally active, 5-9 check. See man.
     --weather-unit   Set weather units to metric (m), imperial (i), metric/imperial (mi), or imperial/metric (im).
 -y, --width          Output line width max (integer >= 80). Overrides IRC/Terminal settings or actual widths. If no integer 
                      give, defaults to 80. -1 removes line lengths. 1 switches output to 1 key/value pair per line. 
                      Example: inxi -y 130 
 -z, --filter         Adds security filters for IP/MAC addresses, serial numbers, location (-w), user home directory name, host 
                      name. Default on for IRC clients. 
     --filter-label   Filters out partition labels in -j, -o, -p, -P, -Sa.
 -Z, --filter-override
                      Override for output filters. Useful for debugging networking issues in IRC, for example.
     --filter-uuid    Filters out partition UUIDs in -j, -o, -p, -P, -Sa.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
Extra Data Options:
 -a, --admin          Adds advanced sys admin data (only works with verbose or line output, not short form); check man page for 
                      explanations!; also sets --extra=3: 
                         -A  If available: list of alternate kernel modules/drivers for device(s).
                         -C  If available: CPU socket type, base/boost speeds (dmidecode+root/sudo/doas[BSDs] required); CPU 
                             vulnerabilities (bugs); family, model-id, stepping - format: hex (decimal) if greater than 9, 
                             otherwise hex; microcode - format: hex. 
                      -d,-D  If available: logical and physical block sizes; drive family; maj:min, USB drive specifics; SMART 
                             report. 
                         -E  If available: in Report:, adds Info: line: acl-mtu, sco-mtu, link-policy, link-mode, 
                             service-classes. 
                         -G  If available: Xorg Display ID, Screens total, default Screen, current Screen; per X Screen: 
                             resolution, dpi, size, diagonal; per Monitor: resolution; hz; dpi; size; diagonal; list of 
                             alternate kernel modules/drivers for device(s). 
                         -I  As well as per package manager counts, also adds total number of lib files found for each package 
                             manager if not -r; adds init service tool. 
                   -j,-p,-P  For swap (if available): swappiness and vfs cache pressure, and if values are default or not.
                         -L  LV, Crypto, devices, components: add maj:min; show full device/components report (speed, mapped 
                             names). 
                      -n,-N  If available: list of alternate kernel modules/drivers for device(s).
                         -o  If available: maj:min of device.
                      -p,-P  If available: raw size of partitions, maj:min, percent available for user, block size of file 
                             system (root required). 
                         -r  Packages, see -Ia.
                         -R  mdraid: device maj:min; per component: size, maj:min, state.
                         -S  If available: kernel boot parameters.

 -x, --extra          Adds the following extra data (only works with verbose or line output, not short form):
                         -A  Specific vendor/product information (if relevant); PCI/USB ID of device; Version/port(s)/driver 
                             version (if available); non-running sound servers. 
                         -B  Current/minimum voltage, vendor/model, status (if available); attached devices (e.g. wireless 
                             mouse, keyboard, if present). 
                         -C  CPU flags (short list, use -f to see full list); CPU boost (turbo) enabled/disabled, if present; 
                             Bogomips on CPU; CPU microarchitecture + revision (if found, or unless --admin, then shows as 
                             'stepping'). 
                         -d  Extra optical drive features data; adds rev version to optical drive.
                         -D  HDD temp with disk data. Kernels >= 5.6: enable module drivetemp if not enabled. Older systems 
                             require hddtemp, run as as superuser, or as user if you have added hddtemp to /etc/sudoers (sudo 
                             v. 1.7 or newer)(BSDs see doas). Example: <username> ALL = NOPASSWD: /usr/sbin/hddtemp 
                         -E  PCI/USB Bus ID of device, driver version, LMP version.
                         -G  Specific vendor/product information (if relevant); PCI/USB ID of device; Direct rendering status 
                             (in X); Screen number GPU is running on (Nvidia only). 
                         -i  For IPv6, show additional scope addresses: Global, Site, Temporary, Unknown. See --limit for large 
                             counts of IP addresses. 
                         -I  Default system GCC. With -xx, also shows other installed GCC versions. If running in shell, not in 
                             IRC client, shows shell version number, if detected. Init/RC type and runlevel (if available). 
                             Total count of all packages discovered in system and not -r. 
                         -j  Add mapped: name if partition mapped.
                         -J  For Device: driver.
                         -L  For VG > LV, and other Devices, dm:
        -m,--memory-modules  Max memory module size (if available), device type.
                         -N  Specific vendor/product information (if relevant); PCI/USB ID of device; Version/port(s)/driver 
                             version (if available). 
                   -o,-p,-P  Add mapped: name if partition mapped.
                         -r  Packages, see -Ix.
                         -R  md-raid: second RAID Info line with extra data: blocks, chunk size, bitmap (if present). Resync 
                             line, shows blocks synced/total blocks. Hardware RAID driver version, bus-ID. 
                         -s  Basic voltages (ipmi, lm-sensors if present): 12v, 5v, 3.3v, vbat.
                         -S  Kernel gcc version; system base of distro (if relevant and detected)
                         -t  Adds memory use output to CPU (-xt c), and CPU use to memory (-xt m).
                      -w,-W  Wind speed and direction, humidity, pressure, and time zone, if available.

-xx, --extra 2        Show extra, extra data (only works with verbose or line output, not short form):
                         -A  Chip vendor:product ID for each audio device.
                         -B  Serial number.
                         -C  L1/L3 cache (if root and dmidecode installed).
                         -D  Disk transfer speed; NVMe lanes; Disk serial number; LVM volume group free space (if available); 
                             disk duid (some BSDs). 
                         -E  Chip vendor:product ID, LMP subversion.
                         -G  Chip vendor:product ID for each video device; OpenGL compatibility version, if free drivers and 
                             available; Xorg compositor; alternate Xorg drivers (if available). Alternate means driver is on 
                             automatic driver check list of Xorg for the device vendor, but is not installed on system; Xorg 
                             dpi. 
                         -I  Other detected installed gcc versions (if present). System default runlevel. Adds parent program 
                             (or tty) for shell info if not in IRC. Adds Init version number, RC (if found). Adds per package 
                             manager installed package counts if not -r. 
                   -j,-p,-P  Swap priority.
                         -J  Vendor:chip-ID.
                         -L  Show internal LVM volumes, like raid image/meta volumes; for LVM RAID, adds RAID report line (if 
                             not -R); show all components > devices, number of 'c' or 'p' indicate depth of device. 
        -m,--memory-modules  Manufacturer, part number; single/double bank (if found).
                         -M  Chassis info, BIOS ROM size (dmidecode only), if available.
                         -N  Chip vendor:product ID.
                         -r  Packages, see -Ixx.
                         -R  md-raid: Superblock (if present), algorithm. If resync, shows progress bar. Hardware RAID Chip 
                             vendor:product ID. 
                         -s  DIMM/SOC voltages (ipmi only).
                         -S  Display manager (dm) in desktop output (e.g. kdm, gdm3, lightdm); active window manager if 
                             detected; desktop toolkit, if available (Xfce/KDE/Trinity only). 
                    --slots  Slot length.
                      -w,-W  Snow, rain, precipitation, (last observed hour), cloud cover, wind chill, dew point, heat index, 
                             if available. 

-xxx, --extra 3       Show extra, extra, extra data (only works with verbose or line output, not short form):
                         -A  Serial number, class ID.
                         -B  Chemistry, cycles, location (if available).
                         -C  CPU voltage, external clock speed (if root and dmidecode installed).
                         -D  Firmware rev. if available; partition scheme, in some cases; disk rotation speed/SSD (if 
                             detected). 
                         -E  Serial number, class ID, HCI version and revision.
                         -G  Serial number, class ID.
                         -I  For 'Shell:' adds ([doas|su|sudo|login]) to shell name if present; adds default shell+version if 
                             different; for 'running in:' adds (SSH) if SSH session; adds wakeups: (from suspend) to Uptime. 
                         -J  If present: Devices: serial number, interface count; USB speed; max power.
        -m,--memory-modules  Width of memory bus, data and total (if present and greater than data); Detail for Type, if 
                             present; module voltage, if available; serial number. 
                         -N  Serial number, class ID.
                         -R  zfs-raid: portion allocated (used) by RAID devices/arrays. md-raid: system md-raid support types 
                             (kernel support, read ahead, RAID events). Hardware RAID rev, ports, specific vendor/product 
                             information. 
                         -S  Panel/tray/bar/dock info in desktop output, if in X (like lxpanel, xfce4-panel, mate-panel); (if 
                             available) dm version number, window manager version number, virtual terminal number. 
                      -w,-W  Location (uses -z/irc filter), weather observation time, altitude, sunrise/sunset, if available.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
Additional Options:
 -h, --help           This help menu.
     --recommends     Checks inxi application dependencies + recommends, and directories, then shows what package(s) you need 
                      to install to add support for that feature. 
 -U, --update         Auto-update inxi. Will also install/update man page. Note: if you installed as root, you must be root to 
                      update, otherwise user is fine. Man page installs require root. No arguments downloads from main inxi git 
                      repo. 
                      Use alternate sources for updating inxi
                          1  Get the git branch one version.
                          2  Get the git branch two version.
                          3  Get the dev server (smxi.org) version.
                     <http>  Get a version of inxi from your own server. Use the full download path, 
                             e.g. inxi -U https://myserver.com/inxi 
 -V, --version        Prints inxi version info then exits.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
Advanced Options:
     --alt            Trigger for various advanced options:
                         40  Bypass Perl as a downloader option.
                         41  Bypass Curl as a downloader option.
                         42  Bypass Fetch as a downloader option.
                         43  Bypass Wget as a downloader option.
                         44  Bypass Curl, Fetch, and Wget as downloader options. Forces Perl if HTTP::Tiny present.
     --bt-tool        [bt-adapter|hciconfig|rfkill] Force use of given tool for bluetooth report.
     --dig            Overrides configuration item NO_DIG (resets to default).
     --display        [:[0-9]] Try to get display data out of X (default: display 0).
     --dmidecode      Force use of dmidecode data instead of /sys where relevant (e.g. -M, -B).
     --downloader     Force inxi to use [curl|fetch|perl|wget] for downloads.
     --force          [dmidecode|hddtemp|lsusb|meminfo|usb-sys|vmstat|wmctl]. 1 or more in comma separated list. Force use of 
                      item(s). See --hddtemp, --dmidecode, --wm, --usb-tool, --usb-sys. 
     --hddtemp        Force use of hddtemp for disk temps.
     --host           Turn on hostname for -S.
     --html-wan       Overrides configuration item NO_HTML_WAN (resets to default).
     --limit          [-1; 1-x] Set max output limit of IP addresses for -i (default 10; -1 removes limit).
     --man            Install correct man version for dev branch (-U 3) or pinxi using -U.
     --no-dig         Skip dig for WAN IP checks, use downloader program.
     --no-doas        Skip internal program use of doas features (not related to starting inxi with doas).
     --no-host        Turn off hostname for -S. Useful if showing output from servers etc. -z triggers --no-host.
     --no-html-wan    Skip HTML IP sources for WAN IP checks, use dig only, or nothing if --no-dig.
     --no-man         Disable man install for all -U update actions.
     --no-ssl         Skip SSL certificate checks for all downloader actions (Wget/Fetch/Curl/Perl-HTTP::Tiny).
     --no-sudo        Skip internal program use of sudo features (not related to starting inxi with sudo).
     --output         [json|screen|xml] Change data output type. Requires --output-file if not screen.
     --output-file    [Full filepath|print] Output file to be used for --output.
     --partition-sort [dev-base|fs|id|label|percent-used|size|uuid|used] Change sort order of partition output. See man page 
                      for specifics. 
     --sensors-default
                      Removes configuration item SENSORS_USE and SENSORS_EXCLUDE. Same as default behavior.
     --sensors-exclude
                      [sensor[s] name, comma separated] Exclude supplied sensor array[s] for -s output (lm-sensors, Linux 
                      only). 
     --sensors-use    [sensor[s] name, comma separated] Use only supplied sensor array[s] for -s output (lm-sensors, Linux 
                      only). 
     --sleep          [0-x.x] Change CPU sleep time, in seconds, for -C (default: 0.35). Allows system to catch up and show a 
                      more accurate CPU use. Example: inxi -Cxxx --sleep 0.15 
     --tty            Forces irc flag to false. Generally useful if inxi is running inside of another tool like Chef or MOTD 
                      and returns corrupted color codes. Please see man page or file an issue if you need to use this flag. 
                      Must use -y [width] option if you want a specific output width. Always put this option first in an option 
                      list. 
     --usb-sys        Force USB data to use only /sys as data source (Linux only).
     --usb-tool       Force USB data to use lsusb as data source [default] (Linux only).
     --wan-ip-url     [URL] Skips dig, uses supplied URL for WAN IP (-i). URL output must end in the IP address. See man. 
                      Example: inxi -i --wan-ip-url https://yoursite.com/ip.php 
     --wm             Force wm: to use wmctrl as data source. Default uses ps.
     --wrap-max       Set maximum width where inxi autowraps line starters (previously --indent-min). Current: 90
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
Debugging Options:
     --dbg            Specific debuggers, change often. Only 1 is constant:
                          1  Show downloader output. Turns off quiet mode.
     --debug          Triggers debugging modes.
                        1-3  On screen debugger output.
                         10  Basic logging.
                         11  Full file/system info logging.
                      The following create a tar.gz file of system data, plus inxi output. To automatically upload debugger 
                      data tar.gz file to ftp.smxi.org: inxi --debug 21 
                         20  Full system data collection: /sys; xorg conf and log data, xrandr, xprop, xdpyinfo, glxinfo etc.; 
                             data from dev, disks, partitions, etc. 
                         21  Upload debugger dataset to inxi debugger server automatically, removes debugger data directory, 
                             leaves tar.gz debugger file. 
                         22  Upload debugger dataset to inxi debugger server automatically, removes debugger data directory and 
                             debugger tar.gz file. 
     --debug-proc     Force debugger parsing of /proc as sudo/doas/root.
     --debug-proc-print
                      To locate file that /proc debugger hangs on.
     --debug-no-exit  Skip exit on error to allow completion.
     --debug-no-proc  Skip /proc debugging in case of a hang.
     --debug-no-sys   Skip /sys debugging in case of a hang.
     --debug-sys      Force PowerPC debugger parsing of /sys as sudo/doas/root.
     --debug-sys-print
                      To locate file that /sys debugger hangs on.
     --ftp            Use with --debugger 21 to trigger an alternate FTP server for upload. Format: [ftp.xx.xx/yy]. Must 
                      include a remote directory to upload to. Example: inxi --debug 21 --ftp ftp.myserver.com/incoming 
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
```

Let's see some examples of its use:

**Get the contents of the mirrorlist files:**

```
inxi -r
```

```
Repos:     Active pacman repo servers in: /etc/pacman.d/mirrorlist 
           1: https://america.mirror.pkgbuild.com/$repo/os/$arch
           2: https://mirror.wdc1.us.leaseweb.net/archlinux/$repo/os/$arch
           3: https://mirror.mia11.us.leaseweb.net/archlinux/$repo/os/$arch
           4: https://iad.mirrors.misaka.one/archlinux/$repo/os/$arch
           5: https://mirror.dal10.us.leaseweb.net/archlinux/$repo/os/$arch
           6: https://mirrors.mit.edu/archlinux/$repo/os/$arch
           7: https://mirror.kaminski.io/archlinux/$repo/os/$arch
           8: https://mirrors.rit.edu/archlinux/$repo/os/$arch
           9: http://iad.mirrors.misaka.one/archlinux/$repo/os/$arch
           10: https://arlm.tyzoid.com/$repo/os/$arch
           11: http://arlm.tyzoid.com/$repo/os/$arch
           12: http://mirror.wdc1.us.leaseweb.net/archlinux/$repo/os/$arch
           13: http://mirror.dal10.us.leaseweb.net/archlinux/$repo/os/$arch
           14: http://mirrors.advancedhosters.com/archlinux/$repo/os/$arch
           15: http://mirror.mia11.us.leaseweb.net/archlinux/$repo/os/$arch
           16: https://mirror.stephen304.com/archlinux/$repo/os/$arch
           17: http://mirrors.rit.edu/archlinux/$repo/os/$arch
           18: http://mirror.stephen304.com/archlinux/$repo/os/$arch
           19: http://plug-mirror.rcac.purdue.edu/archlinux/$repo/os/$arch
           20: https://repo.ialab.dsu.edu/archlinux/$repo/os/$arch
           21: http://mirrors.mit.edu/archlinux/$repo/os/$arch
           22: https://mirror.sfo12.us.leaseweb.net/archlinux/$repo/os/$arch
           23: http://mirror.kaminski.io/archlinux/$repo/os/$arch
           24: https://arch.hu.fo/archlinux/$repo/os/$arch
           25: https://mirror.lty.me/archlinux/$repo/os/$arch
           26: https://mirrors.xtom.com/archlinux/$repo/os/$arch
           27: http://il.us.mirror.archlinux-br.org/$repo/os/$arch
           28: http://ca.us.mirror.archlinux-br.org/$repo/os/$arch
           29: http://mirror.sfo12.us.leaseweb.net/archlinux/$repo/os/$arch
           30: https://mirror.netcologne.de/archlinux/$repo/os/$arch
           31: http://mirror.lty.me/archlinux/$repo/os/$arch
           32: http://mirror.arizona.edu/archlinux/$repo/os/$arch
           33: https://mirror.arizona.edu/archlinux/$repo/os/$arch
           34: http://arch.mirror.constant.com/$repo/os/$arch
           35: http://mirrors.xtom.com/archlinux/$repo/os/$arch
           36: https://mirror.bethselamin.de/$repo/os/$arch
           37: https://mirror.pkgbuild.com/$repo/os/$arch
           38: https://mirror.ubrco.de/archlinux/$repo/os/$arch
           39: https://mirror.kumi.systems/archlinux/$repo/os/$arch
           40: https://mirror.f4st.host/archlinux/$repo/os/$arch
           41: https://arch.jensgutermuth.de/$repo/os/$arch
           42: https://ftp.halifax.rwth-aachen.de/archlinux/$repo/os/$arch
           43: https://mirror.fra10.de.leaseweb.net/archlinux/$repo/os/$arch
           44: https://plug-mirror.rcac.purdue.edu/archlinux/$repo/os/$arch
           45: http://arch.hu.fo/archlinux/$repo/os/$arch
           46: https://mirror.chaoticum.net/arch/$repo/os/$arch
           47: https://mirror.wtnet.de/arch/$repo/os/$arch
           48: https://mirror.selfnet.de/archlinux/$repo/os/$arch
           49: https://mirror.23media.com/archlinux/$repo/os/$arch
           50: https://mirrors.ocf.berkeley.edu/archlinux/$repo/os/$arch
           51: https://ftp.fau.de/archlinux/$repo/os/$arch
           52: https://packages.oth-regensburg.de/archlinux/$repo/os/$arch
           53: http://mirror.united-gameserver.de/archlinux/$repo/os/$arch
           54: http://mirror.23media.com/archlinux/$repo/os/$arch
           55: http://mirrors.n-ix.net/archlinux/$repo/os/$arch
           56: http://ftp.fau.de/archlinux/$repo/os/$arch
           57: https://archlinux.thaller.ws/$repo/os/$arch
           58: http://archlinux.thaller.ws/$repo/os/$arch
           59: http://packages.oth-regensburg.de/archlinux/$repo/os/$arch
           60: http://mirror.netcologne.de/archlinux/$repo/os/$arch
           61: https://dist-mirror.fem.tu-ilmenau.de/archlinux/$repo/os/$arch
           62: http://mirror.kumi.systems/archlinux/$repo/os/$arch
           63: https://mirror.pseudoform.org/$repo/os/$arch
           64: https://mirror.gnomus.de/$repo/os/$arch
           65: http://mirror.ubrco.de/archlinux/$repo/os/$arch
           66: https://mirrors.lug.mtu.edu/archlinux/$repo/os/$arch
           67: http://mirror.f4st.host/archlinux/$repo/os/$arch
           68: http://mirror.fra10.de.leaseweb.net/archlinux/$repo/os/$arch
           69: http://archlinux.honkgong.info/$repo/os/$arch
           70: https://mirrors.niyawe.de/archlinux/$repo/os/$arch
           71: http://mirror.chaoticum.net/arch/$repo/os/$arch
           72: https://phinau.de/arch/$repo/os/$arch
           73: http://phinau.de/arch/$repo/os/$arch
           74: http://mirror.selfnet.de/archlinux/$repo/os/$arch
           75: https://arch.mirror.zachlge.org/$repo/os/$arch
           76: http://mirror.wtnet.de/arch/$repo/os/$arch
           77: http://ftp.halifax.rwth-aachen.de/archlinux/$repo/os/$arch
           78: http://arch.mirror.zachlge.org/$repo/os/$arch
           79: http://mirrors.niyawe.de/archlinux/$repo/os/$arch
           80: http://mirrors.ocf.berkeley.edu/archlinux/$repo/os/$arch
           81: http://mirrors.lug.mtu.edu/archlinux/$repo/os/$arch
           82: https://iad.mirror.rackspace.com/archlinux/$repo/os/$arch
           83: http://iad.mirror.rackspace.com/archlinux/$repo/os/$arch
           84: http://mirror.cs.pitt.edu/archlinux/$repo/os/$arch
           85: https://dfw.mirror.rackspace.com/archlinux/$repo/os/$arch
           86: http://ord.mirror.rackspace.com/archlinux/$repo/os/$arch
           87: http://mirrors.liquidweb.com/archlinux/$repo/os/$arch
           88: http://mirror.cc.columbia.edu/pub/linux/archlinux/$repo/os/$arch
           89: https://mirror.satis-faction.de/archlinux/$repo/os/$arch
           90: http://mirror.hackingand.coffee/arch/$repo/os/$arch
           91: https://mirror.hackingand.coffee/arch/$repo/os/$arch
           92: http://ftp.sudhip.com/archlinux/$repo/os/$arch
           93: https://ftp.sudhip.com/archlinux/$repo/os/$arch
           94: http://dfw.mirror.rackspace.com/archlinux/$repo/os/$arch
           95: https://ord.mirror.rackspace.com/archlinux/$repo/os/$arch
           96: http://mirrors.acm.wpi.edu/archlinux/$repo/os/$arch
           97: http://mirror.mikrogravitation.org/archlinux/$repo/os/$arch
           98: https://mirror.mikrogravitation.org/archlinux/$repo/os/$arch
           99: http://repo.ialab.dsu.edu/archlinux/$repo/os/$arch
           100: http://mirror.es.its.nyu.edu/archlinux/$repo/os/$arch
           Active pacman repo servers in: /etc/pacman.d/reborn-mirrorlist 
           1: http://osdn.mirror.constant.com/storage/g/r/re/rebornos/repo/RebornOS/
           2: https://mirrors.dotsrc.org/osdn/storage/g/r/re/rebornos/repo/RebornOS/
           3: https://mirrors.tuna.tsinghua.edu.cn/osdn/storage/g/r/re/rebornos/repo/RebornOS/
           4: https://mirrors.xtom.com.hk/osdn//storage/g/r/re/rebornos/repo/RebornOS/
           5: https://mirrors.bfsu.edu.cn/osdn/storage/g/r/re/rebornos/repo/RebornOS/
           6: https://mirror.liquidtelecom.com/osdn/storage/g/r/re/rebornos/repo/RebornOS/
           7: https://ftp.jaist.ac.jp/pub/sourceforge.jp/storage/g/r/re/rebornos/repo/RebornOS/
           8: http://ftp.halifax.rwth-aachen.de/osdn/storage/g/r/re/rebornos/repo/RebornOS/
           9: http://mirroronet.pl/pub/mirrors/sourceforge.jp/storage/g/r/re/rebornos/repo/RebornOS/
           10: https://ftp.acc.umu.se/mirror/osdn.net/storage/g/r/re/rebornos/repo/RebornOS/
           11: http://osdn.mirror.constant.com/storage/g/r/re/rebornos/repo/RebornOS/
           12: http://mirror.math.princeton.edu/pub/osdn/storage/g/r/re/rebornos/repo/RebornOS/
           13: https://plug-mirror.rcac.purdue.edu/osdn/storage/g/r/re/rebornos/repo/RebornOS/
           14: https://mirrors.gigenet.com/OSDN/storage/g/r/re/rebornos/repo/RebornOS/
           15: https://openbsd.c3sl.ufpr.br/osdn/storage/g/r/re/rebornos/repo/RebornOS/
           16: http://razaoinfo.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/
           17: http://versaweb.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/
           18: http://phoenixnap.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/
           19: http://newcontinuum.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/
           20: http://downloads.sourceforge.net/rebornos/r/RebornOS/
           21: http://cfhcable.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/
           22: http://astuteinternet.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/
           23: http://vorboss.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/
           24: http://freefr.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/
           25: http://netcologne.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS
           26: http://netix.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/
           27: http://excellmedia.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/
           28: http://liquidtelecom.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/
           29: https://jztkft.dl.sourceforge.net/project/rebornos/r/RebornOS/
           30: http://sourceforge.mirror.iweb.com/project/rebornos/r/RebornOS/
           31: https://deac-riga.dl.sourceforge.net/project/rebornos/r/RebornOS/
           32: http://tenet.dl.sourceforge.net/project/rebornos/r/RebornOS/
           33: https://nchc.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/
           34: https://kent.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/
           35: https://jaist.dl.sourceforge.net/sourceforge/rebornos/r/RebornOS/
           36: https://repo.rebornos.org/RebornOS
```

**View the host name, the kernel version in use, if we use a 32 or 64 bit version, the desktop in use, and the name of the distribution used:**

```
inxi -S
```

```
System:    Host: rebornos-user Kernel: 5.11.15-arch1-2 x86_64 bits: 64 Desktop: GNOME 40.1 Distro: RebornOS RebornOS Rolling
```

**Computer information: model, serial number, mobo, BIOS manufacturer (date and version). To use this option you must use sudo:**

```
sudo inxi -M
```

```
Machine:   Type: Desktop System: Hewlett-Packard product: p7-1269c v: N/A serial: MXZ35107DD 
           Mobo: MSI model: 2AE0 v: 1.0 serial: N/A UEFI: AMI v: 7.11 date: 08/31/2012
```

**Processor information:**

```
inxi -C
```

```
CPU:       Info: Quad Core model: AMD A10-5700 APU with Radeon HD Graphics bits: 64 type: MCP cache: L2: 2 MiB 
           Speed: 1397 MHz min/max: 1400/3400 MHz Core speeds (MHz): 1: 1397 2: 1431 3: 1397 4: 1397
```

**Sound card used, sound driver, webcam available, sound server used:**

```
inxi -A
```

```
Audio:     Device-1: Advanced Micro Devices [AMD] FCH Azalia driver: snd_hda_intel 
           Device-2: KYE Systems (Mouse Systems) iSlim 1320 type: USB driver: snd-usb-audio,uvcvideo 
           Sound Server-1: ALSA v: k5.11.15-arch1-2 running: yes 
           Sound Server-2: PulseAudio v: 14.2 running: yes
```

**Available disk drives:**

```
inxi -D
```

```
Drives:    Local Storage: total: 7.28 TiB used: 892.71 GiB (12.0%) 
           ID-1: /dev/sda vendor: Seagate model: ST2000DM008-2FR102 size: 1.82 TiB 
           ID-2: /dev/sdb vendor: Seagate model: ST2000DM006-2DM164 size: 1.82 TiB 
           ID-3: /dev/sdc vendor: Hitachi model: HUA722020ALA331 size: 1.82 TiB 
           ID-4: /dev/sdd vendor: Hitachi model: HUA722020ALA331 size: 1.82 TiB
```

**Information about available network cards:**

```
inxi -N
```

```
Network:   Device-1: Qualcomm Atheros AR8161 Gigabit Ethernet driver: alx 
           Device-2: Ralink RT5390 Wireless 802.11n 1T/1R PCIe driver: rt2800pci
```

**General information of the computer being used:**

```
inxi -b
```

```
System:    Host: rebornos-rafa Kernel: 5.11.15-arch1-2 x86_64 bits: 64 Desktop: GNOME 40.1 Distro: RebornOS RebornOS Rolling 
Machine:   Type: Desktop System: Hewlett-Packard product: p7-1269c v: N/A serial: <superuser required> 
           Mobo: MSI model: 2AE0 v: 1.0 serial: <superuser required> UEFI: AMI v: 7.11 date: 08/31/2012 
CPU:       Info: Quad Core AMD A10-5700 APU with Radeon HD Graphics [MCP] speed: 1397 MHz min/max: 1400/3400 MHz 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Trinity [Radeon HD 7660D] driver: radeon v: kernel 
           Device-2: KYE Systems (Mouse Systems) iSlim 1320 type: USB driver: snd-usb-audio,uvcvideo 
           Display: x11 server: X.Org 1.20.11 driver: loaded: ati,radeon unloaded: fbdev,modesetting,vesa 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: AMD ARUBA (DRM 2.50.0 / 5.11.15-arch1-2 LLVM 11.1.0) v: 4.3 Mesa 21.0.2 
Network:   Device-1: Qualcomm Atheros AR8161 Gigabit Ethernet driver: alx 
           Device-2: Ralink RT5390 Wireless 802.11n 1T/1R PCIe driver: rt2800pci 
Drives:    Local Storage: total: 7.28 TiB used: 892.65 GiB (12.0%) 
Info:      Processes: 256 Uptime: 2m Memory: 15.07 GiB used: 2.52 GiB (16.7%) Shell: Bash inxi: 3.3.04
```

**Memory usage and CPU processes:**

```
inxi -t cm
```

```
Processes: CPU top: 5 of 241 
           1: cpu: 14.9% command: chrome pid: 1740 
           2: cpu: 8.7% command: chrome pid: 1834 
           3: cpu: 7.6% command: chrome pid: 1914 
           4: cpu: 7.5% command: gnome-shell pid: 1297 
           5: cpu: 4.3% command: chrome pid: 2157 
           System RAM: total: 15.07 GiB used: 2.49 GiB (16.5%) 
           Memory top: 5 of 241 
           1: mem: 356.5 MiB (2.3%) command: chrome pid: 1740 
           2: mem: 297.5 MiB (1.9%) command: gnome-shell pid: 1297 
           3: mem: 191.6 MiB (1.2%) command: jackett pid: 769 
           4: mem: 182.7 MiB (1.1%) command: chrome pid: 1950 
           5: mem: 181.2 MiB (1.1%) command: chrome pid: 2144
```

**CPU temperature and fan speed**

```
inxi -s
```

```
Sensors:   System Temperatures: cpu: 4.4 C mobo: N/A gpu: radeon temp: 4.0 C 
           Fan Speeds (RPM): N/A
```


