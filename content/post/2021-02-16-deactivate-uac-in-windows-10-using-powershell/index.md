---
title: "Deactivate UAC in Windows 10 using Powershell"
date: "2021-02-16"
categories: 
  - "the-stuff"
tags: 
  - "administration"
  - "powershell"
coverImage: "pixabay.category.administration.dark_.png"
---

First of all: UAC has its purpose!

But as I consider myself an IT Pro and while I'm installing/deinstalling more software than an average user and need to run some scripts in an admin context: I decided to turn it off on my machine.

And as a fan of powershell, I wanted to do that on the console.  
Here's how.

```powershell
Set-ItemProperty -Path REGISTRY::HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies\System -Name ConsentPromptBehaviorAdmin -Value 0
```

So long ...
