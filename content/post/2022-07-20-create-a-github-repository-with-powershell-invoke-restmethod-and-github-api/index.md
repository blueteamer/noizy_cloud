---
title: "Create a GitHub repository with PowerShell Invoke-RestMethod and GitHub API"
date: "2022-07-20"
tags: 
  - "tools"
  - "github"
  - "powershell"
---

Making REST calls and remotely creating a GitHub repository? I'll get you covered.

<!--more-->
## Table of content 
{{< toc >}}

## What we will talk about

There are many REST APIs out there. And PowerShell is a great tool to automate stuff. Therefore, REST API and PowerShell are a pretty neat combination.

We'll see as an example how to leverage the GitHub REST API to create a new remote repository on GitHub.com.

## What we need

### A Personal Access Token from GitHub

How to get one? Here's how:

![](images/2022-07-15.Default.03.gif)

Getting a Private Access Token from GitHub.com

### REST API Endpoint

The endpoints provide the functionality - or at least the possibility to call the function. For this example it's:

**https://api.github.com/user/repos**

### Header and Body for our REST call

For anyone who does not know how REST calls are working, you might want to check that out before. If you just want to get to the solution stay with me and simply accept that a REST call has a header that usually contains stuff for authorization and authentication, and on the other side there is the body that also contains information that is sent to the endpoints.

```powershell
# REST Endpoint 
$endpoint = "https://api.github.com/user/repos"

# Header 
$headers = @{
  "Authorization" = "token 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"
}

# Body 
$body = @{
  "name" = "NameOfMyNewRemoteRepository"
  "private" = $true
}
```

**Important |** I noticed that for the body the keys are case sensitive. So **name** is working, but **Name** is not. **private** is working, **Private** is not. Keep that in mind.

## Calling the REST

So, now we have everything we need to create a remote repository on GitHub.com. Let's see what the script will look like.

```powershell
# Full script 
$endpoint = "https://api.github.com/user/repos" 
$headers = @{
  "Authorization" = "token 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"
}
$body = @{
  "name" = "NameOfMyNewRemoteRepository"
  "private" = $true
}

Invoke-RestMethod -Method "POST" -Headers $headers -Body ($body | ConvertTo-Json) -Uri $endpoint
```

You can put this into a function and use some parameters to make it more flexible.  
And that's it. So long...
