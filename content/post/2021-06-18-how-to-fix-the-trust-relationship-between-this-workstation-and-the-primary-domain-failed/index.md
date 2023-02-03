---
title: "How to fix 'The trust relationship between this workstation and the primary domain failed.'"
date: "2021-06-18"
tags: 
  - "administration"
coverImage: "2021-06-18.exxeta.02.png"
---

This error can possibly occure when a workstation has not been able to connect to the domain controller for some time.

In my case this happend in my lab environment, as I haven't been using it for a while.
<!--more-->
## Fix this issue with PowerShell

I had this issue when trying to login with the domain user "blackmesa\\administrator" on my SQL server (sql.blackmesa.lab). My domain controller is named "dc.blackmesa.lab". This is relevant for the script to be used.

So I had to login with the local admin account ".\\administrator" on sql.blackmesa.lab and opened up a PowerShell console.

```powershell
$domainAdminCredentials = Get-Credentials
```

Now enter the credentials of a valid domain administrator within your network and use it for the next statement.

```powershell
Reset-ComputerMachinePassword -Server "dc.blackmesa.lab" -Credentials $domainAdminCredentials
```

Wait for the statement to finish and you're good to go.

## Alternative via UI

You can also login to your domain controller and remove and add the machine from the AD manually. But if you ask me, this is somehow lame.

So long and happy troubleshooting...
