---
title: "How to restrict a specific Windows Update from installing"
date: "2021-04-16"
categories: 
  - "the-stuff"
tags: 
  - "patching"
  - "security"
  - "windows-10"
---

Windows 10 is pretty straight forward in terms of updates. Update is available, update will be installed.

Actually, that is a really nice thing as it will lessen the number of unpatched Windows 10 systems in the wild.

Unfortunatelly, Microsoft does not practice TDD anymore (at least it seems so). And so it's also pretty common that system or product updates can break stability or functionality.

Therefore it makes sense to prohibit specific updates to be installed on the system.

Latest case was the infamous KB5000802 Security Update which leads to a complete system crash if you try to print something. This happend to the laptop of my wife several times as uninstalling the update directly lead to automatic reinstall done by Windows 10 itself.

In an enterprise environment you have way more possibilities to control what will be installed. In private you don't.

But as usual:

## PowerShell to the rescue

Use the PowerShell Module PSWindowsUpdate to "hide" a specific update and it will be ignored by the Windows Update Service on your machine.

Open a PowerShell Console on your machine.

```powershell
# You need elevated permissions. 
# So in case you forgot about that use
Start-Process PowerShell -Verb RunAs 
```

Now, we're going to install the PowerShell module and tell Windows 10 to ignore the bad boy Security Update KB5000802.

```powershell
# Install the module 
Set-ExecutionPolicy Unrestricted
Install-Module "PSWindowsUpdate"

# Let's see what Updates are installed/available 
Get-WUList 

# Tell Windows Update Service to ignore the update
Hide-WindowsUpdate -KBArticle KB5000802 
```

Btw, the workaround to have the fixed Security Update installed is awkward: You have to install it manually.

Go to "Windows Update" on your machine and search for the latest Windows Updates. Check out the "optional" updates. There will be an **optional update for march**. This will fix the fix.

So long and happy patching...
