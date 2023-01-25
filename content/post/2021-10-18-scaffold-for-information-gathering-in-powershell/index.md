---
title: "Scaffold for information gathering in PowerShell"
date: "2021-10-18"
categories: 
  - "the-stuff"
tags: 
  - "powershell"
  - "sharepoint"
---

It’s a common task to get information out of your SharePoint Server farm or SPO tenant and process the outcome in other tools or make a report out of it.

**Note |** You will find a lot of examples of how to get information from your SharePoint farm and a huge amount of it recommend using an array to hold the data and Add-Member to but build your custom report PowerShell object. Please don’t do that. An array can be used when you have a fixed count of items. Information gathering is always a dynamic procedure where an unidentified number of items will be added to your array. Add-Member is a legacy from - I dunno - PowerShell 2.0? There are more elegant ways to add properties to a custom object in PowerShell nowadays.

## The scenario

We will get all site collections of a SharePoint Server farm, read some properties out of that and hold the result in an array list (not to be confused with an array).

```powershell
# Get all site collections from farm 
$sitecollections = Get-SPSite -WebApplication "https://url.to-spwebapplication.tld" -Limit All 

# Create results object of type arraylist 
$result = New-Object -TypeName "System.Collections.ArrayList"

# iterate through all site collections and get some info 
foreach ($site in $sitecollections) {
    # define property and assign values 
    $property = [ordered]@{
        Name = $site.Title 
        Url = $site.Url 
    }
    
    # create object to which properties will be attached 
    $resultObject = New-Object -TypeName psobject -Property $property 
    
    # store information in results arraylist 
    $result.Add($resultObject) 
}

# Export result as csv file 
$result | Export-Csv "D:\path\to\my\file.csv" -NoTypeInformation
```

## Conclusion

For the sake of demonstration, the above code is ok. But in a real-world scenario, you would probably have to make some adjustments. Like using parameters, output and stuff...

Hope this will help anyone out there. Cheers!
