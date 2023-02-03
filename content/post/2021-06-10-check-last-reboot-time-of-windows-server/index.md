---
title: "Check last reboot time of Windows Server"
date: "2021-06-10"
tags: 
  - "troubleshooting"
---

A few weeks ago I came to work and was told that a customer SharePoint server was not working properly. Great news to start a Monday morning.

When I connected to the server via RDP I could see that the server was rebooted - but I was not told when or why. To investigate why the server was rebooted it is good to know when the server was booted.

<!--more-->

Let's have a look at how to do that with PowerShell.

## Get reboot time of server via PowerShell

Start a PowerShell console or connect via Enter-PSSession and type this:

```powershell
Get-EventLog -LogName System | Where-Object {$_.EventID -in (6005,6006,6008,6009,1074,1076)} | Format-Table TimeGenerated,EventID,Message -AutoSize -Wrap
```

The EventIDs mentioned above indicate the reboot time of the server.

Now you can narrow down the timeframe where the issue might happen and properly find the root cause of the unexpected reboot.

Alternatively, you can use this in the command line :

```bash
systeminfo | find /i "Boot Time" 
```

Happy troubleshooting.
