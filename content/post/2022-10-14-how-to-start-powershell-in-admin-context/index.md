---
title: "How to start PowerShell in admin context"
date: "2022-10-14"
categories: 
  - "the-stuff"
---

Sometimes we need to execute statements in PowerShell as admin.

And yes, you can right-click on the PowerShell entry, select "run as Administrator" and you're good to go. But let's have a look at how to do that directly from the terminal (common user context).

```powershell
Start-Process powershell -verb runas
```

That's it.

Of course, you need sufficient permission to do so - but besides that should work like a charm.

So long.
