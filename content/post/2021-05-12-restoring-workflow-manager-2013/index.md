---
title: "Restoring Workflow Manager 2013"
date: "2021-05-12"
tags: 
  - "sharepoint"
---

Believe it or not: Workflow Manager 2013 is still the recommended Workflow Engine for SharePoint On-Prem (even for SharePoint 2019). I'm no big fan of this construct for it is a quite difficult to administer piece of software.

But it's part of the SharePoint ecosystem, so let's take a look at how to install it.

<!--more-->

_Disclaimer: There are plenty of instructions out in the web. But most of them are out-dated and the latest version of Workflow Manager components need some extra info to be stressed so everything works smoothly._

## The pieces

For using Workflow Manager 2013 we need to have two components installed in our farm:  
1\. Azure Service Bus 1.1  
2\. Workflow Manager 1.0 (CU2) with TLS  
These are installed by using the Web Platform Installer provided by Microsoft. Nowadays it's a bit tricky to get the right stuff installed because when you start the Web Platform Installer and search for Service Bus or Workflow Manager you will get a result list with a lot of different versions and CUs. It is key to select the correct one as you will receive weird error messages and install break downs if you try to install the wrong version.

For now (2021-May-12) you need to install "Windows Azure Pack: Service Bus 1.1 with TLS 1.2 Support" and "Workflow Manager 1.0 Refresh (CU2)".

After that you should also install the latest updates.

![](images/install.workflowmanager.01-1024x586.png)

Windows Azure Pack: Service Bus 1.1 with TLS 1.2 Support

![](images/install.workflowmanager.00-1024x562.png)

Workflow Manager 1.0 Refresh (CU2)

## Install Workflow Manager 2013

When I'm installing the Workflow Manager I usually do the following:

- Start Web Platform Installer as Administrator (right click -> Run as Administrator)
- Search for **"Service Bus"** in WebPI
- Select **"Windows Azure Pack: Service Bus 1.1 with TLS 1.2 Support"**
- Install the selected package
- Reboot
- Again, start WebPI as Administrator
- Search for **"Workflow Manager"**
- Select **"Workflow Manager 1.0 Refresh (CU2)"**
- Install the selected package
- Run the configuration wizard for Workflow Manager (if it's a brand new environment)
- Abort the configuration wizard for Workflow Manager (if I'm going to do a restore) and do the restore by hand (more about that in one of the upcoming posts)
- Reboot

## Conclusion

Installing Workflow Manager 2013 isn't very complicated if you know what to install - this was something I struggled a lot in the beginning as most of the instructions out there point to out-dated packages. And trying to install them resulted in missing dependencies (for instances).

Next step is to configure the Service Bus Farm, the Workflow Manager Farm and connect everything with SharePoint.

So long...
