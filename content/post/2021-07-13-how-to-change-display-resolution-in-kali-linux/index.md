---
title: "How to change display resolution in Kali Linux"
date: "2021-07-13"
tags: 
  - "kali"
---

When I installed Kali Linux lately on Hyper-V I realized that the resolution of the RDP session (opened within Hyper-V Manager) was stuck to 1024x768. I was not able to make any - obvious - change somewhere. And to be honest: 1024x768 was just not enough for me.

<!--more-->

## Change the resolution

We have to make a modification to a config for grub and restart the machine.  
Therefore go to your Kali Linux machine and open a terminal.

```bash
# Open the grub config file
john@kali:~$ sudo nano /etc/default/grub 
```

Search for a line similar to this

```vim
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```

Possible that there are more parameters after "quiet". But this is the line we need to modify.  
So change this line to the following:

```vim
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=hyperv_fb:1920x1080"
```

**Info** | In my case I switched the resolution to 1920x1080. I haven't tested any higher resolutions. So, can't tell if it's working with higher numbers.  
Let me know if you have any experience with that.

Save the modification with nano's shortcuts **Ctrl+X** and confirm with **y**.

Now update the change for grub with this statement

```bash
john@kali:~$ sudo update-grub
```

After a restart of your Kali Linux machine, the new settings should apply and you'll now have way more place on your desktop.

Enjoy.

## Reference

\[1\] [Change Kali Linux screen resolution on Hyper-V Virtual Machine](https://www.youtube.com/watch?v=N8K9qnd5NT8) (Youtube: HERESJAKEN)
