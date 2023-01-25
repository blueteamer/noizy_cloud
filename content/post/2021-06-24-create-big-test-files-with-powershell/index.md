---
title: "Create big test files with PowerShell"
date: "2021-06-24"
categories: 
  - "the-stuff"
tags: 
  - "powershell"
---

I recently needed some files for testing purposes and I wondered if there is a way to create such files with PowerShell.

And of course, there is.

```powershell
# Create a 1 GB test file with PowerShell 
$path = "c:\development\testfiles\a-hugh-1-gb-file.avi" 
$file = [IO.File]::Create($path)
$file.SetLength(1gb) 
$file.Close() 

# Let's grab that file 
$item = Get-Item $path 
```

That's just an example of how to do this. The best would be to make it configurable and create files of various sizes. And also directly upload the files to a SharePoint document library.

As soon as I have done this, I'll update this post.

So long...
