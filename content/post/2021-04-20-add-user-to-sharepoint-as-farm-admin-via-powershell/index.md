---
title: "Add user to SharePoint as Farm Admin via PowerShell"
date: "2021-04-20"
categories: 
  - "the-stuff"
tags: 
  - "managing-sharepoint"
  - "powershell"
  - "security"
---

What do you do, if you need to add a user to SharePoint as Farm Admin but you don't want to open Central Admin?

Use SharePoint PowerShell.

```powershell
# Get a list of all webapplications incl. CA 
Get-SPWebApplication -IncludeCentralAdministration 

# Take the url of CA to get the Central Administration web app 
$ca = Get-SPWebApplication -Identity "https://linktosharepoint.ca" 

# Now get the web object 
$caweb = Get-SPWeb -Identity $ca.Url 

# From the web we can get the required SharePoint Group
# and add the user to that group 
$user = "DOMAIN\first.last" 
$spgroup = $caweb.SiteGroups["Farm Administrators"] 
$spgroup.AddUser($user, "", $user, "") 
```

And voila! Your user is a Farm Admin now.

## Hint

Please consider using Active Directory security groups for such scenarios. The steps described above are possible but not recommended.

So long...
