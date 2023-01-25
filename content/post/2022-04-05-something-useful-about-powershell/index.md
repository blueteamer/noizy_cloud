---
title: "Something useful about PowerShell"
date: "2022-04-05"
categories: 
  - "the-stuff"
tags: 
  - "powershell"
---

One thing I've learned as a developer is: You don't need to know every single property and method of a class - you only need to know where to look it up.

True for so many different topics. And today's topic is PowerShell.

## Working our way through

Imagine you want to start with a PowerShell Module called ImportExcel. The first thing to do is check if it's already installed.

```powershell
Get-Module -ListAvailable | Where-Object {$_.Name -like "*excel*"}
```

Assume it is not installed. Now we want to install it but we don't know the exact name. So let's have a quick search.

```powershell
Find-Module -Name "*excel*"
```

This will bring up all the modules in the PowerShell Gallery which have something excel-ish in their name. Get the right one - in our instance "ImportExcel".

```powershell
Install-Module -Name "ImportExcel"
```

And if you want the module to be used just in your user context instead of for all users on the machine:

```powershell
Install-Module -Name "ImportExcel" -Scope "CurrentUser" 
```

Alrighty. Now we have the module "ImportExcel" up and ready to use.

But how do I know what methods and properties an object does have?

```powershell
$myobject | Get-Member | Format-Table
```

... will do the trick.

Last but not least, there is probably any kind of help documentation.

```powershell
Get-Help Import-Excel -Full
```

That's it.  
Good stuff.  
So long.
