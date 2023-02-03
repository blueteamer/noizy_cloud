---
title: "How to get Feature Solutions from SharePoint Farm"
date: "2021-04-09"
tags: 
  - "sharepoint"
---

One part of a SharePoint Migration or Upgrade is to configure the target similiar to the source. And in most cases there will be some custom feature solutions deployed on the source.

But how can I get those feature solutions to install them on the target?

<!--more-->
## Table of content 
{{< toc >}}

Of course, the technical responsible for SharePoint should have that \*.wsp file somewhere. But often nobody knows where the installation files are saved.

## PowerShell for the rescue

You can use SharePoint PowerShell to extract the \*.wsp file from the existing SharePoint.

Let's check out how to do that.

In our example we assume we're coping with a SharePoint Feature solution called sharepoint.hoppdidoodledydoop.wsp.

```powershell
# Access the local SharePoint Farm 
$farm = GetSPFarm
$solutionfile = $farm.Solutions.Item('sharepoint.hoppdidoodledydoop').SolutionFile 
$farm.SaveAs('d:\pathtomy\solutions\sharepoint.hoppdidoodly.wsp') 
```

Take the \*.wsp file, copy it to the target farm and install the solution.

```powershell
# Adding the solution to the solution catalog 
Add-SPSolution -Literalpath 'd:\pathtomy\solutions\sharepoint.hoppdidoodly.wsp') 
Install-SPSolution -Identity 'sharepoint.hoppdidoodly.wsp' -CompatibilityLevel 14, 15, 16 -GAC
```

Now you are able to attach the Content Database and perform the upgrade.

Let me know, if this approach has worked for you.

So long...
