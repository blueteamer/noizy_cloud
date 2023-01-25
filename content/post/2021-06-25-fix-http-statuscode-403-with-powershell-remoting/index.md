---
title: "Fix \"HTTP-Statuscode 403\" with PowerShell Remoting"
date: "2021-06-25"
categories: 
  - "the-stuff"
tags: 
  - "powershell"
  - "troubleshooting"
---

I had some trouble connecting via RDP to a SharePoint Server. When I tried to get access to that machine via PowerShell to restart the RDP service I received the following error.

![](images/2021-06-24.consulting.psremotingerror.05.png)

Connecting to remote server XYZ failed with the following error message: The WinRM client received an HTTP status code of 403 from the remote WS-Management service.

After some digging, I found the following situation fits my issue.

The workstation I was using was configured to use an HTTP proxy. And it seems PowerShell has beef with that configuration.

## How to fix this

First, check if a proxy is configured for you.

```powershell
netsh winhttp show proxy
```

This will show you any proxy configured for your machine. If this applies to you, then get rid of the proxy first:

```powershell
netsh winhttp reset proxy
```

If this worked, you will see something like "DirectAccess (no proxy server)" in the console.

Next, try to connect to the machine via PS Remoting.

```powershell
# Read the credentials via a popup window
$usercredentials = Get-Credential
Enter-PSSession -ComputerName mymachine.domain.tld -Credential $usercredentials 
```

Your console prompt should now show you something like this.

```powershell
[mymachine.domain.tld]: PS C:\Users\master.admin\Documents> _
```

Now you can do whatever your user is allowed to do on that machine.

So long...
