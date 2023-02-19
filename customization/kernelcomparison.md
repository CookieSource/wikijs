---
title: Kernel Comparison
description: Compare the different kernels we offer
published: true
date: 2023-02-19T08:05:21.402Z
tags: customization, installation, kernels
editor: markdown
dateCreated: 2023-02-18T16:54:09.780Z
---

# Officially supported kernels 

RebornOS officially supports the following kernels.

1.  Stable
2.  LTS
3.  Zen
4.  Hardened

# Kernel comparisons 

Below we provide info on the supported and other popular 3rd party kernels. However it should be noted that the stable and LTS kernels are generally what we recommend to use.

As they are well tested and will generally work on most hardware.

## Stable

Vanilla Linux kernel and modules, with a few patches applied.

### How to install Stable

Stable should be installed by default.

```plaintext
sudo pacman -S linux
```

Afterwards be sure to boot from it during startup!

## LTS

Long-term support (LTS) Linux kernel and modules.

### How to install LTS

LTS can be installed with the command

```plaintext
sudo pacman -S linux-lts
```

Afterwards be sure to boot from it during startup!

## Zen Kernel

Result of a collaborative effort of kernel hackers to provide the best Linux kernel possible for everyday systems.

### How to install Zen

 Zen can be installed with the command

```plaintext
sudo pacman -S linux-zen
```

Afterwards be sure to boot from it during startup!

## Hardened kernel

A security-focused Linux kernel applying a set of hardening patches to mitigate kernel and userspace exploits. It also enables more upstream kernel hardening features than Linux.

### How to install Hardened kernel

Linux Hardened can be installed with the command

```plaintext
sudo pacman -S linux-hardened
```

Afterwards be sure to boot from it during startup!

## Clear

The Clear Linux kernel provides Patches from Intel's Clear Linux project which improves the performance and security of Intel CPUs in most cases.

### How to install Clear

The Clear kernel is only available in the AUR

Use your preferred AUR helper. We used yay in the example below

```plaintext
yay -S linux-clear
```

Afterwards be sure to boot from it during startup!

## TKG

A highly customizable kernel build system that provides a selection of patches and tweaks aiming for better desktop and gaming performance.

### How to install TKG

The TKG kernel is only available in the AUR

We need to build TKG from their repository.

```plaintext
git clone https://github.com/Frogging-Family/linux-tkg.git
cd linux-tkg
makepkg -si
```

Afterwards be sure to boot from it during startup!

## Xanmod

Aiming to take full advantage in high-performance workstations, gaming desktops, media centers and others and built to provide a more rock-solid, responsive and smooth desktop experience.

### How to install Xanmod

The Xanmod kernel is only available in the AUR

Use your preferred AUR helper. We used yay in the example below

```plaintext
yay -S linux-xanmod
```

Afterwards be sure to boot from it during startup!

## Cacule

Cacule is a kernel that tries to enhance system performance, responsiveness and latency.

### How to install Cacule

The Cacule kernel is only available in the AUR

Use your preferred AUR helper. We used yay in the example below

```
yay -S linux-cacule
```

Afterwards be sure to boot from it during startup!