---
title: "How to Start Powershell in Admin Context"
description: 
date: 2022-10-14T12:00:00+01:00
image: /header/cyber_01.jpg
draft: false
tags: 
- powershell
---

Sometimes we need to execute statements in PowerShell as admin. 
<!--more-->
And yes, you can right-click on the PowerShell entry, select “run as Administrator” and you’re good to go. But let’s have a look at how to do that directly from the terminal (common user context).

```powershell {style=nord}
Start-Process powershell -verb runas
```

That’s it.

Of course, you need sufficient permission to do so – but besides that should work like a charm.

So long.