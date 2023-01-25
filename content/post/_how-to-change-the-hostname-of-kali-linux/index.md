---
title: "How to Change the Hostname of Kali Linux"
description: 
date: 2022-12-02T00:00:00+01:00
image: /default-header.png
draft: false
tags: 
- linux
- demo2
---

Let’s assume you have installed a Kali Linux machine with a hostname of “attackbox”. And now you want to change it to something more – let’s say – dramatic. For instance: “thedestroyer”.


|Old hostname |New hostname  |
|---|---|
|attackbox| thedestroyer|
 

Nothing easier than that (and we’re going to do it in a terminal session):

``` bash {style=nord}
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

So long…