---
title: Gaming
description: Setup your RebornOS for gaming
published: true
date: 2022-12-17T13:59:03.793Z
tags: gaming, games
editor: markdown
dateCreated: 2022-12-14T09:46:09.728Z
---

# Gaming

The following information is a general guideline to prepare your RebornOS installation to be able to support playing games, including games that may only be allowed to run on Windows.

## Requirements

Before you can start playing 3D games you should be familiar with your basic system hardware.  One way to view the hardware configuration is to use the *inxi* application to see what the system's hardware capabilities are.  Some systems might not have a *discrete graphics adapter,* and thus your gaming experience might not be as good or enjoyable without having one.  Remember it is very important to always check minimum and recommended game requirements first, with the game publisher before attempting game play.  If your system doesn't meet minimum system requirements, most likely that game may not run, or it might run, but be very crippled and game play will be impacted.  Also, be aware that not all games can run on Linux, mostly due to the game developer's [Anti-Cheat](https://areweanticheatyet.com/) implementation, (not due to lack of hardware requirements).   But, overall you should still be able to play a large variety of games, some less graphic demanding games, or even adjust the settings to be able to launch and play 3D games with some reasonable enjoyment.

Run the *inxi* application to provide you with that basic information.  You would want to note the CPU, CPU chipset or architecture, the amount of system RAM, the graphics adapter, and lastly your network, to be able to verify and check what the minimum or recommended hardware is needed to be able to play that or other similar game.  It's also good to know this information if you need to do further troubleshooting, in case you experience a problem running a game.

```plaintext
inxi -b
```

After viewing the information you should at least know the system's hardware specifications and can now start installing the necessary files to allow your RebornOS to be gaming enabled.

If you find your system doesn't meet the minimum graphics card requirement or your favorite games aren't supported due to Anti-Cheat, there might still be a way to play 3D games by streaming them over the network.  Solutions such as Steam (has the ability to stream over a network), [GeForce NOW](https://discord.com/channels/805020018537660416/805020019083313156/1025681457605263381), and Parsec are other examples. 

## Updating the system

Run pacman to update the repository:

```plaintext
sudo pacman -Syy
```

Update the graphics adapter files, specifically DXVK, (DirectX Vulkan), which are necessary to support Windows games, thus depending on the result of your inxi -b output choose the appropriate files to update your graphics adapter.

AMD Graphics:

```plaintext
sudo pacman -S lib32-mesa vulkan-radeon lib32-vulkan-radeon vulkan-icd-loader lib32-vulkan-icd-loader
```

For Nvidia, you might need to [check what driver version](https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/) your card needs if it is from an older architecture (GTX 900 or older) thus you may need 470.xx or 390.xx driver packages:

```plaintext
sudo pacman -S nvidia nvidia-utils lib32-nvidia-utils nvidia-settings vulkan-icd-loader lib32-vulkan-icd-loader
```

Intel Graphics, if you have a Skylake CPU or newer the iGPU will be able to use Vulkan, if Haswell, there is minimal Vulkan support and gaming performance may be lacking.

```plaintext
sudo pacman -S lib32-mesa vulkan-intel lib32-vulkan-intel vulkan-icd-loader lib32-vulkan-icd-loader
```

After the graphic updates, perform a system reboot.  Next, we normally will install Steam, Heroic Games Launcher, Lutris, and Wine to be able to support the majority of the game libraries available as well as support other game utilities or applications under Wine.

Steam - there is an extensive game library from Valve Software and they have their Proton libraries to enable Windows game capability, including game streaming.  You should check that your system meets the [minimum system requirements.](https://github.com/ValveSoftware/steam-for-linux#readme)

```plaintext
sudo pacman -S steam 
```

Heroic Games Launcher - this is an all-in-one game launcher and has extensive capabilities including, but not limited to Epic Games Launcher, GOG, syncing your accounts, Epic and GOG game stores, support for Legacy (command line which allows some support for EasyAntiCheat, and BattleEye AntiCheat in some titles), Wine Manager (Wine-GE, Proton-GE), ability to install other games as well as link your existing installed Steam library games.  
  
For Heroic Game Launcher, install via Gnome Software store, AUR, Flatpak, or use the AppImage.

Example using AUR:

```plaintext
yay -S heroic-games-launcher-bin
```

Flatpak:

```plaintext
sudo pacman -S flatpak
sudo flatpak install com.heroicgameslauncher.hgl
```

  Lastly, it's recommended to have Wine, Lutris and Gamemode (Feral Interactive) to round out the full capability for gaming on Linux.

```plaintext
sudo pacman -S wine-staging wine-gecko wine-mono lutris gamemode lib32-gamemode
```

## Start gaming

After installation, if not already done, you should create your logins for Steam, Epic Games, GOG, and Lutris.  Then launch Steam to verify access to your game library, and do the same for Heroic Games Launcher to link your Epic Games Launcher and GOG libraries.  If you have these existing accounts, HGL will populate both libraries and display your games.  If you have local games already installed you can add them in HGL or in Lutris.

Remember, check the game requirements with your system information to see if your system meets the minimum.  
Another good resource is to look at the [ProtonDB](https://protondb.com) for more information about game compatibility. 

If you encounter troubles, have questions, or just a comment about your experience, please post in the [RebornOS Discourse Forum](https://rebornos.discourse.group), or for more immediate issues please visit the RebornOS Discord under 'gaming' or ‘help and support’ for assistance. 

Happy gaming! 

The following links were used and referenced to write this:

[https://winehq.org](https://winehq.org)

[https://github.com/ValveSoftware/steam-for-linux](https://github.com/ValveSoftware/steam-for-linux)

[https://github.com/doitsujin/dxvk](https://github.com/doitsujin/dxvk)

[https://heroicgameslauncher.com](https://heroicgameslauncher.com)

[https://lutris.net](https://lutris.net)

[https://steamcommunity.com/sharedfiles/filedetails/?l=german&id=1787799592](https://steamcommunity.com/sharedfiles/filedetails/?l=german&id=1787799592)

[https://github.com/lutris/docs](https://github.com/lutris/docs)

[https://github.com/FeralInteractive/gamemode](https://github.com/FeralInteractive/gamemode)