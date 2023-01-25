---
title: "Black screen after logging in via RDP"
date: "2021-10-08"
categories: 
  - "the-stuff"
---

Lately, I encountered a problem while trying to log into a Windows Server 2019 via RDP. Logging in seemed to be working fine. But in the end, all I had was a black screen.

## First attempt

I thought this might be a problem with the RDP Service running on this machine and decided to restart that service. And I used PowerShell to do so.

```powershell
# Connect to the weirdo computer via PowerShell Remoting 
c:\> Enter-PSSession -Computer funny.behaviour.server -Credential (Get-Credentials) 
c:\> Restart-Service -Name "termservice" -Force
```

So the RDP Service was restarted - but nothing changed.

## Second try

Then, I remembered that I have read about the strange behaviour of RDP if you still have a session open on the server where you want to log in. That meant: Check the existing sessions on the weirdo server and kill them if necessary.

```powershell
# I'm using the connection from above 
c:\> quser 
USERNAME      SESSIONNAME      ID      STATE      IDLE TIME      LOGON TIME      
funny.admin                     4      Disc               .      05.09.2021 11:38
```

It seems I have a session running for my **funny.admin** user. Let's kill that session and try re-logging via RDP. For that, we need the ID. In this case **4**.

```powershell
c:\> logoff 4
```

Done.

The next attempt to log in via RDP was successful and the black screen was replaced with the Windows Server Desktop.

Problem solved. So long...
