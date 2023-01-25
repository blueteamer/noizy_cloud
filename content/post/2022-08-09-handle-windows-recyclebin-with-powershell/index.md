---
title: "Handle Windows RecycleBin with PowerShell"
date: "2022-08-09"
categories: 
  - "the-stuff"
tags: 
  - "powershell"
---

Access to the Windows Recycle Bin via PowerShell can come in handy for a mere of situations.

## Why should I care?

The Recycle Bin can be of interest in many cases.

- troubleshooting
- research
- a user lost a file

Well, actually in any case you need access to deleted files or you need extra free space on a machine - in which case you can empty the recycle bin.

**But why via PowerShell?** In some situations, you might access systems without a GUI (Windows Server) or you are connected to the target via PowerShell remoting.

## How to do it?

I won't get into how to connect to a remote machine via PowerShell remoting. That's described in another blog post.

```
# Create an object representing the recycle bin 
$shell= New-Object -ComObject shell.application
$recyclebin = $shell.Namespace(10) 

# Show content of recyclebin and filter by name
$recyclebin.Items() | Where-Object {$_.Name -like "*something*"} 

# For emptying the recycle bin, there is a predefined cmdlet 
Clear-RecycleBin -Force 

# whitch will empty the the RecycleBin instantly 
```

## References

- **[Clear-RecycleBin](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-7.2)** (Microsoft)  
    \[https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-7.2\]
