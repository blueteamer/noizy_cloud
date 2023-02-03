---
title: "How to import CSV file in PowerShell"
date: "2021-06-28"
tags: 
  - "powershell"
---

It's a common task to import values from a CSV file and process them in a PowerShell script. Here's how.

<!--more-->

```powershell
# Define the path to a user list as csv file
$filepath = "c:\users\themighty.one\desktop\users.csv
$filecontent = Import-Csv -Path $filepath -Delimiter ";" 

# Filter the content by the column 'userlogin'
$userlogins = $filecontent | select userlogin 

foreach ($userlogin in $userlogins) {
    # Do something fancy with the userlogin
}
```

## Some thoughts on this

In this example we assume a structure in the CSV file like this one:

```powershell
firstname;lastname;userlogin;status;
homer;simpson;homer.simpson;pending;
marge;simpson;marge.simpson;pending;
monty;burns;monty.burns;pending
```

Though the 'c' in CSV stands for comma, it is often the case that a different character is used as a delimiter. So have a look inside of the file to check what is used in your case.

The rest is pretty straightforward. As I only need the user login values I can do a 'select' and work only with the user logins.

So, enjoy your life and happy scripting...
