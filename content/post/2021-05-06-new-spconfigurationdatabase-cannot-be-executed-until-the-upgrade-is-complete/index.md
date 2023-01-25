---
title: "New-SPConfigurationDatabase cannot be executed until the upgrade is complete"
date: "2021-05-06"
categories: 
  - "the-stuff"
tags: 
  - "administration"
  - "powershell"
  - "sharepoint"
---

I had a SharePoint Server that had - unexpectedly - installed several updates. After that the SharePoint farm was in a quite messy state. I was hopping from one exception to the next one while trying to fix the platform.

At some point I decided let's start from the beginning and do a restore of the content databases.

Problem: After setting everything back, I tried to setup a new Farm Config DB (btw... Backup concept was on-going to that time :( ).

## Solution

```powershell
psconfig -cmd upgrade -inplace b2b -wait -force
```

But be aware! Running this command will lead to another error message that the upgrade could not be performed on any database - which is of course because there is currently now database to perform that action on.

Anyway. Running this command above does the trick.

## Background

The statement above does not only perform some actions on the database but also modifies several registry key entries on the local server which tells the SharePoint Management Console that the current state of the server is somewhere in between a upgrade process.

Hopes that helped some you, too.

So long...
