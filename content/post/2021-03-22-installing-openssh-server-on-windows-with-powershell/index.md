---
title: "Installing OpenSSH Server on Windows with PowerShell"
date: "2021-03-22"
categories: 
  - "the-stuff"
tags: 
  - "powershell"
---

I'm not certainly sure if this is even necessary. But I'm pretty sure there will be a use-case for installing OpenSSH Server on a Windows machine somewhere in production.

In my case I needed a way to connect to my private lab server via mobile. And as there are a lot of good ssh and telnet implementation for android, I decided to go with OpenSSH server.

Therefore I wrote a script which is doing the install and configuration of OpenSSH server on my machine.

If you want to use that code, make sure you are running PowerShell as Administrator.

```powershell
$server = Get-WindowsCapability -Online | Where-Object {'Name' -like 'OpenSSH.Server*' }

if ($server.State -ne 'Installed') {
    #Install OpenSSH Server 
    Add-WindowsCapability -Online -Name 'OpenSSH.Server~~~~0.0.1.0'

    #Configure OpenSSH Server 
    Start-Service sshd
    Set-Service -Name sshd -StartupType 'Automatic' 

    #Setup Firewall rule to use OpenSSH server
    $sshNetRule = Get-NetFirewallRule | Where-Object {'Name' -like "OpenSSH-Server-In-TCP" }
    if (!$sshNetrule.Enable) {
        New-NetFirewallRule -Name sshd -DisplayName "OpenSSH Server (sshd)" -Enabled $true -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
    }
}
```

Maybe this is something that could help you, too.

So long...
