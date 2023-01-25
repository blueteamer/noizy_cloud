---
title: "Kali Linux 2022.3 not loading in Hyper-V"
date: "2022-10-05"
categories: 
  - "the-stuff"
tags: 
  - "hyper-v"
  - "linux"
  - "troubleshooting"
---

I was re-building my lab environment when I realized that the installation of Kali Linux 2022.3 didn't work as expected.

## So, what happened?

In the past

- Create a Hyper-V Gen 1 vm with 2 cores and 4096 MB RAM

- Assigned eth with inet access

- installed xrdp

- configured grub to load video=hyperv\_fb:1920x1080

- GNOME Desktop

Now, that doesn't seem to work anymore

## Solution

Create a Hyper-V Gen 2 VM and deactivate the Secure Boot option.

That's it!

So long...
