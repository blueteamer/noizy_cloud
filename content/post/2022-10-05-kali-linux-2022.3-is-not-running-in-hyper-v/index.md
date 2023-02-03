---
title: "Kali Linux 2022.3 Is Not Running in Hyper V"
description: 
date: 2022-10-05T12:00:00+01:00
#image: /default-header.png
image: /header/cyber_06.jpg
draft: true
tags: 
- "kali linux"
---

I was re-building my lab environment when I realized that the installation of Kali Linux 2022.3 didn’t work as expected.
<!--more-->
So, what happened?

In the past

- Create a Hyper-V Gen 1 vm with 2 cores and 4096 MB RAM
- Assigned eth with inet access
- installed xrdp
- configured grub to load video=hyperv_fb:1920×1080
- GNOME Desktop
- Now, that doesn’t seem to work anymore

Solution
- Create a Hyper-V Gen 2 VM and deactivate the Secure Boot option.

That’s it!

So long…


