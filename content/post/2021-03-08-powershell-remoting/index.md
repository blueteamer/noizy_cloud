---
title: "PowerShell Remoting"
date: "2021-03-08"
tags: 
  - "administration"
coverImage: "pixabay.category.administration.dark_.png"
---

PS-Remoting can be used to execute PowerShell scripts from your machine on a remote computer. This comes especially in handy as soon as we are talking about administration of multiple machines within a network. Let's take a deeper look on this topic in this post. 

<!--more-->
## Table of content
{{< toc >}}

## Remote Desktop vs. PowerShell Remoting

Usually you are using Remote Desktop to connect to a remote machine and do your administrative tasks that way - and there is nothing wrong with that.

The great advantage of PowerShell Remoting lies in its ability to support script based automation - by nature.

Instead of doing configurations and administrations on each and every single machine step by step, you can create a generic PowerShell script to do all that stuff for you and let this script be run on all affected machines via PowerShell remoting.

You can see a practical application of PowerShell Remoting within the Microsoft Azure environment. Most of the automated communication between machines is done there by using PowerShell Remoting.

## Security

PowerShell Remoting is based on **Windows Remote Management** (WinRM) which for itself is Microsofts implementation of the open standard of the WS-Management Protocol.

It’s a well tested and established way of connecting systems.

There are also several options to configure PowerShell Remoting in terms of accessibility of resources. For instance, you can setup your infrastructure that scripts can only be executed from specific IP and specific users. A common requirement as soon as you have external companies involved in managing your network and/or servers.

![](images/consultinginsights.powershellremoting.examplesnetworksetup-1024x506.png)

Example Network Setup

That makes it easy to control who can do what without making everything to complicated.

After all, it’s definitely worth a look and should be part of every administrator working with Windows Server environments.

### References

Microsoft Doc | ["Windows Remote Management" (2021-03-05)](https://docs.microsoft.com/en-us/windows/win32/winrm/portal)  
Microsoft Doc | ["Security Considerations for PowerShell Remoting using WinRM" (2021-03-05)](https://docs.microsoft.com/en-us/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-7.1)
