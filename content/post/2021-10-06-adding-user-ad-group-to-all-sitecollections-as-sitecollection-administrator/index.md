---
title: "Adding user/ad group to all sitecollections as sitecollection administrator"
date: "2021-10-06"
categories: 
  - "the-stuff"
tags: 
  - "administration"
  - "powershell"
  - "sharepoint"
---

A typical task in reorganizing an already existing SharePoint farm is to add a specific user or AD group as a site collection administrator.

The best way to do this is by leveraging PowerShell.

```powershell
<#
    Add user as site collection administrator to 
    all site collections of web application 
    v1.0 
    October 2021 
#>

# Get parameter for reusability of this script 
param 
(
    [parameter(mandatory=$true)]
    [string]$username,
    [parameter(mandatory=$true)]
    [string]$webapplicationUrl 
)

# Load SharePoint PowerShell thingies 
Add-PSSnapin -Name "microsoft.sharepoint.powershell" 

$webapplication = Get-SPWebApplication -Identity $webapplicationUrl 
if ($webapplication -eq $null) {
    Write-Host "Error. Webapplication with URL '$($webapplicationUrl)' does not exist. " -ForegroundColor Red
    break
}
else {
    Write-Host "Done. " -ForegroundColor Green
}

# Iterate through all site collections and assign user as site collection admin 
foreach ($sitecollection in $webapplication.Sites) {
    $adminuser = $sitecollection.RootWeb.EnsureUser($username) 

    # Add user if not already a site collection admin 
    if ($adminuser.IsSiteAdmin -eq $true) {
        Write-Host "User '$($adminuser)' is already site collection admin in '$($sitecollection.Url)'. "         
    }
    else {
        $adminuser.IsSiteAdmin = $true 
        $adminuser.Update()
        Write-Host "User '$($adminuser)' is now site collection admin on '$($sitecollection.Url)'. "
    }
}

```

So long...
