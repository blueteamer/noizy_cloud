---
title: "Create, set and use Windows environment variables in PowerShell"
date: "2022-07-13"
categories: 
  - "the-stuff"
tags: 
  - "powershell"
---

For several reasons - e. g. in development and infrastructure configuration - environment variables are used to have some flexibility with values in scripts.

Let's see how to create new ones, set existing ones and use them in our PowerShell script.

## The example

In our example, we are going to create a Windows environment variable to store our GitHub Private Access Token and use it in a script to get information via GitHub API.

**Important |** I know, I know. This example is total BS and a huge security flaw. "You should use a Credential Manager. Blah bla bla.", some might say.  
Yes, you're right. But for the sake of this example let's imagine nobody would ever take advantage of a key stored in plain text in an environment variable.

So, we're going to create an environment variable called **demogithubpat** with the value of **ghp\_6vfb3SEQf7Lhs0obkE8JJQBxCy1aQf52u1Lg** (just for demo purposes).

<table><tbody><tr><td><strong>Variable Name</strong></td><td>demogithubpat</td></tr><tr><td><strong>Variable Value</strong></td><td>ghp_6vfb3SEQf7Lhs0obkE8JJQBxCy1aQf52u1Lg</td></tr></tbody></table>

## Get all existing environment variables in PowerShell

First of all, let's check what environment variables are at present on our machine. To get that info, we leverage the so-called providers in PowerShell. For environment variables, it's the **ENV:** provider. But there are several others e. g. **Registry** for the Windows Registry.

```powershell
# Get a list of all existing environment variabls
Get-ChildItem env:
```

This will bring up a long list of variables with their values. Not gonna put a screenshot of mine for obvious reasons.

**Note |** You want a list of all available providers? **Get-PSProvider** is your friend.

## Create an environment variable with PowerShell

By using the **environment provider** this is pretty straightforward. Remember the values from above?

```powershell
# Creating an environment variable
New-Item -Path env:demogithubpat -Value '	ghp_6vfb3SEQf7Lhs0obkE8JJQBxCy1aQf52u1Lg'
```

When you now check the existence of the new variable with **Get-ChildItem env:**, you will find your new variable with its value in the listing.

**Note |** You can remove the environment variable by using **Remove-Item -Path env:<name-of-your-variable>**.

## Using environment variables in PowerShell scripts

Again, using the provider you can easily reference the value of an environment variable in your PowerShell Script. In this example, we try to create a new private repository named **demo.**

```powershell
# Setting up the header for a GitHub REST call 
$headers = @ {
  Authorization = "token $env:demogithubpat"   #<< here it is
}

# Building up the payload
$body= {
  <# Build some fancy payload #>
}

Invoke-RestMethode -Method 'POST' -Headers $headers -Body $body -Uri "https://risky.but.awesome.github.com/api.call" 
```

## References

- **[Getting started with the REST API](https://docs.github.com/en/rest/guides/getting-started-with-the-rest-api)** (GitHub Docs)  
    \[https://docs.github.com/en/rest/guides/getting-started-with-the-rest-api\]
- **[Invoke-RestMethod](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-7.2)** (Microsoft Docs)  
    \[https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-7.2\]
- **[about\_Environment\_Variables](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-7.2)** (Microsoft Docs)  
    \[https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about\_environment\_variables?view=powershell-7.2\]
