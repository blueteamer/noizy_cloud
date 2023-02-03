---
title: "High CPU usage on SharePoint Server by noderunner.exe"
date: "2022-01-14"
tags: 
  - "administration"
  - "powershell"
  - "sharepoint"
---

I saw this issue for a client's SharePoint Server 2016 farm. The app server had almost all the time a CPU usage of 99%. Looking into it the root for this was a noderunner#2 process which turned out to be SharePoint Search.

<!--more-->

Some googling and I found the advice in a few pretty old blog posts, telling me I should follow these steps:

1. Reduce performance level of search service
2. Modify the config for noderunner.exe (actually to limit the memory usage - so not really an issue for CPU usage)
3. Restart the service

## 1\. Using PowerShell to reduce performance level of SharePoint Search

```
# by setting the performance level to 'reduced' CPU usage should go down - but also search performance will decrease
Set-SPEnterpriseSearchService -PerformanceLevel Reduced
```

**Note |** As already mentioned in the code block, be aware this will also decrease the performance of the search and will likely increase the time when new content will be available in search results.

## 2\. Modify the noderunner.exe.config

This step is widely recommended to limit the memory usage of the SharePoint Search. But again! Keep in mind, that this will also decrease SharePoint's Search feature.

You can find the config file (e.g.) in:

```
C:\Program Files\Microsoft Office Servers\16.0\Search\Runtime\1.0\noderunner.exe.config
```

Look for a node "memorylimitmegabytes". This is initially '0' which means 'unlimited'. Change it to whatever suits you (e.g. 2048 for 2 GB).

Save the file and continue to the last step.

## 3\. Restart SharePoint Search Service

Switch to the PowerShell console and type

```
Restart-Service SPSearchHostController 
```

That's it.

In the best case, you should now experience a CPU working in a "normal" range.

**Note |** Take into consideration, that there might be a lot of different reasons why SharePoint behaves as it does. Maybe your hardware is underpowered. Or a different configuration leads to that high CPU usage. So don't take this solution as the holy grail of SharePoint-CPU-messing-around-fix.

So long...
