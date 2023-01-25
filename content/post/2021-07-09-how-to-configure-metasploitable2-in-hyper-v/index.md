---
title: "How to configure Metasploitable2 in Hyper-V"
date: "2021-07-09"
categories: 
  - "the-stuff"
tags: 
  - "hyper-v"
  - "security"
---

For a demo environment, I needed Metasploitable2 up and running on my Hyper-V host. Doing so bears some pitholes which I'd like to talk about today.

## Metasploitable2 is provided as VMware image

First thing is, that you won't get an ISO or something as this machine is preconfigured and you get a ready-to-use virtual machine. The problem: It's aiming at VMware as a hypervisor. So we have to transform the image to use it with Hyper-V.

Microsoft used to have a tool for that. But I was not able to find a download source, which I could trust enough to get it on my local machine. Therefore the alternative is a tool called "StarWind V2V Converter". (btw. it's free)

## Convert the VMware image to Hyper-V

Download, install and start "StarWind V2V Converter" on your Hyper-V host. Then choose the VMware image as source and the local Hyper-V machine as a target. Some tweaks and you're good to go.

## Configure Metasploitable2 with a static IP

The next issue you will find is: Running under Hyper-V, Metasploitable2 will not show an eth0 network adapter which we can configure to have a static IP. :(

Solution:  
Turn off the Metasploitable2 machine and switch to the settings of the VM. Remove the network adapter and confirm with "Apply".

Next, add a new network adapter - but now choose the "Legacy Network Adapter" from the list provided by Hyper-V. Select the switch you want to use and restart the machine.

Now you should see the eth0 network adapter when you type "ifconfig".

## Configure eth0 with a static IP

**You might want to ask why?**  
Well... Metasploitable2 is a pre-configured Ubuntu that holds a lot of bad web applications. And it's hard to access those web applications from a client if you don't know the address of the server, which hosts all those stuff. Static IP will help us out on this.

The first step is to modify the network adapter config file. We're going to use nano for that (just because I don't like vim. Never liked it ¯\\\_(ツ)\_/¯ )

```bash
# Use sudo to execute the statement in an admin context 
msfadmin@metasploitable:~$ sudo nano /etc/network/interfaces
```

Confirm the statement by entering the admin password (msfadmin) once again.

Now you should see something similar to this:

```bash
# This file describes the network interface available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface 
auto lo
iface lo inet loopback

# The primary network interface 
auto eth0
iface eth0 inet dhcp 


```

We are going to change the last line and add some additional stuff.

The assumption is as followed:

- No usage of DHCP
- New IP: 12.0.0.100
- New Subnet: 255.255.255.0

Therefore change the file like this

```bash
# This file describes the network interface available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface 
auto lo
iface lo inet loopback

# The primary network interface 
auto eth0
iface eth0 inet static
address 12.0.0.100
netmask 255.255.255.0
```

Save the file with Ctrl + X

You might need to restart the network adapter.

```bash
# shutdown the network adapter 
msfadmin@metasploitable:~$ sudo ifdown eth0 

# bring it back to live 
msfadmin@metasploitable:~$ sudo ifup eth0

# check network adapter values 
msfadmin@metasploitable:~$ ifconfig 
```

- [![](images/2021-07-09_23h24_15-150x150.png)](https://consulting-insights.de/wp-content/uploads/2021/07/2021-07-09_23h24_15.png)
    
    Before
    
- [![](images/2021-07-09_23h39_28-150x150.png)](https://consulting-insights.de/wp-content/uploads/2021/07/2021-07-09_23h39_28.png)
    
    After
    

Now you can use any browser within the same network to access the website provided by Metasploitable2 by typing "http://12.0.0.100"

So long...
