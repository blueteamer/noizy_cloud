---
title: "Keep your SharePoint server clean"
date: "2021-04-23"
tags: 
  - "sharepoint"
---

As a consultant, it doesn't happen quite often that you come to a client and you can set up a SharePoint environment from scratch. More often you may find a more or less "OK" setup of SharePoint and network infrastructure.

Therefore, here are some recommendations from my side. They are not complete and not definite - just recommendations.

<!--more-->
## Table of content 
{{< toc >}}

## Remove unused application pools and sites

In a default setup of a SharePoint server, you will find a lot of unnecessary application pools and websites. Unless you have some specific use cases for them, get rid of them.

![](images/article.keepyoursharepointserverclean-1024x333.png)

Removed the default site and all the out-of-the-box application pools.

There are a lot of recommendations regarding the application pools. If you don't have the most strict requirements regarding security you can keep the number of application pools pretty low which is good for your performance on the server. If you need to keep each and every service separated, you might think of a distributed architecture and spread the pressure over several servers within your farm.

## Use Active Directory Security Groups

Use them. Just use them! Active Directory is made for managing accounts, access and policies. So, why not use them.

A lot of companies are using SharePoint in-build groups to manage access to specific content within their collaboration platform. Unfortunately, this usually ends up in an unmanageable mess of user access and no one knows where to start fixing this.

Be smart and think of a system before you implement SharePoint in your company.

Security groups don't cost any additional money, so there is no problem to extensively include them in your permission concept. I would even go that far, to have an Active Directory sec group created for every SharePoint group in each SiteCollection or Web. Combine that with a provisioning tool for SharePoint Sites and you have an easy way to keep control of who has access to what.

## Remove any obsolete files

Sometimes when I'm doing troubleshooting for customers I stumble upon leftovers from other consulting companies. Lately, I found a folder that was clearly used for AutoSPInstaller for setting up the SharePoint farm. As I was curious what was left I took a peek inside and found the config file - including information of service users and passwords. Even as this is not that a big deal in terms of security, there was account information mentioned which provides a user elevated privileges.

Just keep your mess down! You have finished your project? Clean up.

## Use smart account names

spfarm. Who is spfarm?

This is also something that drives me nuts. Active Directory provides you the ability to use up to 20 characters for an account. Make use of them. There is a difference between a workflow.farmadmin and a sharepoint.farmadmin. More often than not you will find a spfarm as service account and as SharePoint farm admin. So, what is the purpose of the account? Is it the farm administrator or a service account? You cannot tell just by the name.

Don't get me wrong. You can name your accounts like whatever you want. As far as you keep track of them in good documentation. And let's be honest: Most companies don't document.

So think of a speaking name and place them in a good OU within your Active Directory. This will make it easier for later to see what was the purpose of this account.

## Use an automated provisioning mechanism for SharePoint

You can do a lot in SharePoint. And you can do a lot as a simple user. And this will lead to a mess of site collections, sub-sites, folders, lists. Some are used solely for testing purposes.

An automated mechanism with some kind of a regulatory overwatch can help you to keep your SharePoint cleaner.

Make it request based. Use the requests as inventory. Implement a life cycle management.  
This can easily be done with a PowerShell based solution for smaller environments or a Farm Solution for enterprise-sized companies.

## Separate Test and Production

Spend the money and set up a second (Single Server) Farm for testing and development purposes. There is nothing worse than mixing up not-working-development-stuff, half-baked-testing-sites and completely messed up production environments.

## Don't ignore patching

I know. This topic is hated - but do it on a regular base anyways. Not only for security reasons but also for the sake of stability of your system. And here comes the test environment in handy. Do some research and check out the impact of the patches on your test environment before you're going to install them on production.

## Conclusion

There is a lot of stuff you can do to keep your environment clean. And the best thing is: The less stuff is on your system, the less you have to worry about in case something goes wrong.

So long...
