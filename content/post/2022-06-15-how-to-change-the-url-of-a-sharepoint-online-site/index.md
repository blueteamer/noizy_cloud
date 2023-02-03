---
title: "How to change the URL of a SharePoint Site"
date: "2022-06-15"
tags: 
  - "sharepoint"
---

Sometimes you might feel the urge of changing the URL of an existing SharePoint Online site. Though I recommend not to do that - unless you have a good reason - here's how to do a change.

<!--more-->
## Table of content 
{{< toc >}}

For the sake of demonstration

<table><tbody><tr><td>Old URL</td><td>https://customername.sharepoint.com/sites/commstuff</td></tr><tr><td>New Url</td><td>https://customername.sharepoint.com/sites/communication</td></tr></tbody></table>

**Note |** Keep in mind: A change of the URL leads to the inaccessibility of resources referenced by URL. For instance links to pages, documents, images, and so on. Take that into consideration before messing around with URL changes.

## SharePoint Admin Center

The first way to change the URL is through the SharePoint Admin Center.

- Open the SharePoint Admin Center (https://customername-admin.sharepoint.com)
- Active Sites
- Click on the site to be modified -> Menu comes up
- In the tab "General" you'll see a link "modify" under URL. Click it.
- Enter the new part for the URL after _domain/sites/_
- Instant check will tell you if the new URL is possible
- Click save and wait some time until changes are applied

## PowerShell

Second way: PowerShell!

Install the SharePoint Online PowerShell module, connect to your tenant and make the changes accordingly. I'll show you in a second through the script part.

**Note |** You need to be SharePoint Online Admin or Global Admin to perform these tasks.

```powershell
# Install the SharePoint Online PowerShell Module 
install-module -name "Microsoft.SharePoint.Online.PowerShell" 
update-module -name "Microsoft.SharePoint.Online.Powershell" 

# Connect to the tenant and provide credentials via pop up window
Connect-SPOService -url "https://customername-admin.sharepoint.com" -Credentials (Get-Credentials) 

# Let's check if we actually can do a mod of the site's URL
Start-SPOSiteRename -Identity "https://customername.sharepoint.com/sites/commstuff" -NewSiteUrl "https://customername.sharepoint.com/sites/communication" -ValidationOnly 
```

The **\-ValidationOnly** part will just check if the URL change is possible or if there are any obstacles. If everything is fine, we can go on.

```powershell
# Do the actuall change of the URL by leaving away the parameter -ValidationOnly 
Start-SPOSiteRename -Identity "https://customername.sharepoint.com/sites/commstuff" -NewSiteUrl "https://customername.sharepoint.com/sites/communication" 
```

**Note |** By using **Get-SPOSite** you will see that the old URL is still listed as Site. Unfortunately, using the SharePoint Admin Center this is sometimes not the case. I couldn't figure out why, yet. It is relevant if you want to switch back to the original URL (e. g. roll back, mistakenly changed the URL or whatever). In this case, the validation in the UI and in PowerShell will tell you the target URL is not available.  
To make it available you need to remove the site listed with the target URL by using  
**Remove-SPOSite -Identity "https://customername.sharepoint.com/sites/commstuff"**

## References

- [Get started with SharePoint Online Management Shell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps) (Microsoft Docs)  
    \[https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps\]
- [Remove-SPOSite](https://docs.microsoft.com/en-us/powershell/module/sharepoint-online/remove-sposite?view=sharepoint-ps) (Microsoft Docs)  
    \[https://docs.microsoft.com/en-us/powershell/module/sharepoint-online/remove-sposite?view=sharepoint-ps\]
- [Change a site address](https://docs.microsoft.com/en-us/sharepoint/change-site-address) (Microsoft Docs)  
    \[https://docs.microsoft.com/en-us/sharepoint/change-site-address\]
