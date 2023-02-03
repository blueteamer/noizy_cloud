---
title: "How to Change the Hostname of Kali Linux"
description: 
date: 2022-12-02T00:00:00+01:00
image: /default-header.png
draft: false
tags: 
- "kali"
---

Sometimes you need to change the hostname of a linux system. Here's how to do that. 
<!--more-->

## Assumptions 
{{<columns>}}
#### Old hostname 
  
attackbox 
  
<--->
  
#### New hostname 
  
thedestroyer
{{</columns>}} 

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
