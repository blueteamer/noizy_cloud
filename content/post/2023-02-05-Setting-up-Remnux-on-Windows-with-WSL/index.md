---
title: "Setting Up REMnux on Windows With WSL"
date: 2023-02-05T16:40:55+01:00
draft: false
tags: 
- REMnux
- tools 
---

REMnux is a toolset for malware analysis and forensics based on Linux. In my lab environment I have a Windows 10 device that I use as a detonation chamber and for quick analysis tasks. Unfortunately, there are not that much tools available which are running purely on Windows OS. Here comes WSL in handy. 

<!--more-->
## Table of content 
{{< toc >}}

## What is WSL?
The Windows Subsystem for Linux (WSL) is a virtualization solution to let Windows host Linux distributions. This offers you a nice amount of additional tools to the tip of your fingeres while still sitting in a Windows environment. 

WSL is a Windows feature that needs to be activated. 

## What is REMnux?
Remnux is a Linux based distro with a lot of tools pre-installed focussing on malware analysis and forensics. The distro was set up and is mainly maintained by Lenny Zeltzer. He's a known SANS instructor and a valuable contributor to the community. 

REMnux holds a lot of tools - most of them command line tools. But there are also UI based tools like Ghidra or Maltego. Additionaly, there are a lot of useful Python scripts. 

{{< hint type=note >}}
Using REMnux via WSL will provide you access to the command line based tools, only. If you want to use solutions provided by REMnux which require a desktop environment, consider using a standalone installation. 
{{< /hint >}}


## Setting up WSL on Windows 
As the Windows Subsystem for Linux is a Windows feature, it is pretty easy to enable the feature via the feature context menu. 

- Activate Windows Subsystem for Linux on Windows Host System 
- Install [Kernel Update Package](https://learn.microsoft.com/en-us/windows/wsl/install-manual) on Host System 


## Install Ubuntu 20.04 
We need to install Ubuntu 20.04 in order to use the REMnux tool set. There are still some dependencies which will not work properly with the latest version of Ubuntu. Nevertheless, you should install the latest security updates for the 20.04 release. 

```
wsl --install -d Ubuntu-20.04 
```

## First run 
- select a user name and a password
- the password is used for elevated activities (root context)

## Update distro 
```
sudo apt update 
sudo apt upgrade 
```

## Install Python2
In case Python2 is not available in the instance, install it via "apt install"

```
sudo apt install python2-minimal 
```

## Install REMnux toolset 
REMnux provides an installer on their web site. 
- Download the installer 
- make the script generally available 
- make the script executable 
- call the script explicitly with **--mode=addon** 

```
# Download REMnux Installer 
wget https://remnux.org/remnux-cli

# rename and relocate script to bin 
mv remnux-cli /usr/local/bin/remnux 

# make the script executable 
chmod +x /usr/local/bin/remux 

# execute installer as root 
sudo remnux install --mode=addon 
```

## Conclusion 
Installing REMnux on Windows Subsystem for Linux is fairly simple and provides a huge set of tools to do forensics and malware analysis. 

I'll try to write about some of those tools in future posts. In the meanwhile: Stay tuned. 

So long... 

## Sources 
- [Remnux](https://remnux.org)
- [Remnux CLI](https://remnux.org/remnux-cli)


