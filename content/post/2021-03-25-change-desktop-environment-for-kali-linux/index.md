---
title: "Change desktop environment for Kali Linux"
date: "2021-03-25"
tags: 
  - "kali linux"
---

Today something a little bit 'off-topic'. :)

Last year I had a little bit of spare time because of all this pandemic stuff. So I decided to take a look into IT security. And if your taking a look at IT security nowadays, it doesn't take long until you step over Kali Linux from Offensive Security.

It's a great toolbox for doing a lot of different security related stuff. So definetly worth taking a deeper look into.

<!--more-->
## Table of content 
{{< toc >}}

## Install KDE

But today we want to take a look at something pretty ordinary regarding Kali Linux. Installing a different desktop environment.In this case: KDE Plasma.

The default desktop environment is xfce. And it's a good environment. Lightweight, straight forward and functional. But sometimes you wanna try out something different.

By the way: All the steps are also valid for GNOME, if you prefere that kind of environment.

So let's start.  
Log into your Kali Linux and start a terminal. We will then update the install package directory and install KDE.

```bash
$ sudo apt update 
$ sudo apt install kali-desktop-kde 
```

For GNOME the last statement would be **kali-desktop-gnome** instead of **kali-desktop-kde**.

Now some installation magic will happen. Until you will be asked which display manager you want to use.  
Select sddm (for KDE) or gnome3 (for Gnome).

Again some installation magic will fight dragons in the background.  
As soon as you have the regular prompt in the terminal which indicates that the install process has been finished, type

```bash
$ reboot
```

to restart the machine.

## Enjoy KDE Plasma

After the reboot you will be prompted for your credentials. In the lower left corner you can select which desktop environment you want to use.  
Select Plasma (that's the KDE desktop).

As there are some known issues if you have Xfce and KDE installed on the same machine, we might get rid of Xface.  
To do so use those commands

```bash
$ sudo apt remove kali-desktop-xfce xfce4* lightdm* 
$ sudo apt autoremove 
```

Hope you enjoyed reading and trying out something new with your Kali machine.  
So long...

## Reference

[\[1\] "How to install KDE \[_sic_\] deskstop on Kali Linux" (2021-Mar-21) | linuxconfig.org](https://linuxconfig.org/how-to-install-kde-dekstop-on-kali-linux)
