---
title: "Startup Script for Hyper-V VMs"
date: "2021-02-10"
categories: 
  - "the-stuff"
tags: 
- "Hyper-V"
coverImage: "pixabay.category.administration.png"
---

Having only one VM on a hypervisor is usually not that pain to turn on and off via PowerShell. This starts to be a issue as soon as we are talking about a whole network of virtual computers. Best case depending on each other. For this it is worth the time to create a PowerShell script this.

<!--more-->

![](images/ExampleNetwork-1-1024x768.jpg)

Example of three computer depending on each other

In this example we have three computer depending on each other in terms of their initiation phase.  
SharePoint depends on the SQL Server, and both depend on the Active Directory Domain Controller.  
Therefore it makes sense to start with the computer 'AD'. Second in line will be the computer 'SQL'. And the last one: 'SP2016'.

So all you need to start a VM is

```powershell
Start-VM -Name "Name-Of-My-VM"
```

To get a list of all VMs on your hypervisor you can use

```powershell
Get-VM
```

Making it a little bit prettier and verbose you can add some descriptive messages as stated in this example:

```powershell
Write-Host -Foregroundcolor Yellow "Starting Vms..."
Start-VM -Name "DC" 
Write-Host -Foregroundcolor Green "Computer 'DC' up and running." 

Start-VM -Name "SQL" 
Write-Host -Foregroundcolor Green "Computer 'SQL' up and running."

Start-VM -Name "SP2016" 
Write-Host -Foregroundcolor Green "Computer 'SP2016' up and running." 

Write-Host -Foregroundcolor Blue -Backgroundcolor Green "VMs successfully started."
```

By the way:  
Having a script to stop the computer is almost the same. But instead of using

```powershell
Start-VM -Name "Name-of-my-computer"
```

use this

```powershell
Stop-VM -Name "Name-of-my-computer"
```

Here is an example of this method (remember to stop the computer in a reverse order)

```powershell
#Stop VMs in a specific order
 Write-Host -Foregroundcolor Yellow "Shutting down VMs…"
 Write-Host -Foregroundcolor Yellow "Shutting down computer 'SP2016'."
 Stop-VM -Name "SP2016" 
 Write-Host -Foregroundcolor Green "Done."
 Write-Host -Foregroundcolor Yellow "Shutting down computer 'SQL'."
 Stop-VM -Name "SQL" 
 Write-Host -Foregroundcolor Green "Done."
 Write-Host -Foregroundcolor Yellow "Shutting down computer 'DC'."
 Stop-VM -Name "DC" 
 Write-Host -Foregroundcolor Green "Done."
 Write-Host -Foregroundcolor Blue -Backgroundcolor Green "VMs successfully stopped."
```

Easy and handy. Hope this could save you some seconds in your life.

So long...

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
\[0\] Microsoft Documentation "Start-VM" ([link](https://docs.microsoft.com/en-us/powershell/module/hyper-v/start-vm?view=win10-ps))  
\[1\] Microsoft Documentation "Stop-VM" ([link](https://docs.microsoft.com/en-us/powershell/module/hyper-v/stop-vm?view=win10-ps))
