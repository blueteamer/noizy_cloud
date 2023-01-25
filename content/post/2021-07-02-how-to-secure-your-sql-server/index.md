---
title: "How to secure your SQL Server"
date: "2021-07-02"
categories: 
  - "the-stuff"
tags: 
  - "active-directory"
  - "network"
  - "security"
  - "sql-server"
---

SQL Server often hosts sensitive data within a company. Reasonable to have a closer look at how to keep these data safe.

## Keep your server up-to-date

This sounds so stupid. But often updates are over-managed in companies so that some updates don't even make it to the critical infrastructure. Don't get too sophisticated about updates. At least security updates should be installed asap. This takes effect for the SQL Server itself, but also for the Windows Server OS.

## Keep your server clean

This is also something which should be totally clear. Keep your SQL Server (actually any server) clean. Only install what is absolutely necessary.  
The best example is SQL Server Management Studio. Don't install it directly on the SQL Server itself. You can use a "management server" to install administrative tools.

And this leads us to another concept...

## Implement a management infrastructure

Try to avoid working directly on your SQL Server. Especially if you have a huge server landscape it's pretty convenient to have a separate environment where you can control access to your production.

Also, you can install all your favorite management tools on those servers and access the machines in the production environment without messing around in a live system.

If you have a staging environment it also comes in handy that you have to set up your management machine only once and can access multiple environments from there.

You might want to make sure PowerShell Remoting is enabled and working. Security can then be applied by using GPO and Active Directory.

![](images/2021-07-02.Default.02-1024x528.png)

Example of a network with management environment

## Keep access to your server restricted

Focus on least privilege concepts and implement a role-based security concept. Try to avoid providing users direct access to your server. Instead, use Active Directory Security Groups.

## Keep SQL Server quiet

You should also deactivate SQL Server Browser to hide any instances. This makes it difficult to find the machines within the network.

## Final thoughts

These are just a few - very simple - measures you can take to make your SQL Server and also other servers more secure. But it's better than nothing.

Consider improving your security skills and harden your network to avoid any messing around later.

So long...
