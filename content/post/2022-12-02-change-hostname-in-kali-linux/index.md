---
title: "Change hostname in Kali Linux"
date: "2022-12-02"
categories: 
  - "the-stuff"
tags: 
  - "kali"
  - "linux"
---

Let's assume you have installed a Kali Linux machine with a hostname of "attackbox". And now you want to change it to something more - let's say - dramatic. For instance: "destroyer".

Old hostname: **attackbox**  
New hostname: **thedestroyer**

Nothing easier than that (and we're going to do it in a terminal session):

```bash
// Get current hostname 
$ hostname
attackbox

// Change the old name in file 'hostname' 
$ sudo nano /etc/hostname 

// Change the old value in file 'hosts' 
$ sudo nano /etc/hosts 

// Reboot the machine 
$ sudo reboot 

// Check change 
$ hostname 
thedestroyer
```

Done.

So long...
