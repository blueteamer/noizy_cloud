---
title: "How to become a SOC analyst?"
date: "2022-10-12"
categories: 
  - "the-stuff"
tags: 
  - "becoming-a-soc-analyst"
---

Part 2 of my posts on how to become a SOC analyst. Today we'll look at some resources I used to start my learning.

## Content

- [What is our goal?](#What-is-our-goal?) 
- [Resources to learn](#Resources-to-learn) 
    - [Defender Ninja Show](#Defender-Ninja-Show) 
    - [Defender Ninja Training](#Defender-Ninja-Training)
    - [SC-900 Training](#SC-900-Training)
    - [Microsoft-Learn](#Microsoft-Learn) 
- [What I would have made differently?](#What-I-would-have-made-differently?)  
- [Final thoughts](#Final-thoughts)
- [References](#References)

## What is our goal?

I want to become a SOC analyst. The environment we are operating in is Microsoft based. That means Microsoft networks with Microsoft clients and servers combined with Microsoft 365 workloads and Azure infrastructure. The Microsoft Defender suite and Sentinel cover almost all of this.

Of course, some Linux machines and compliances also do not run Windows OS on it - but as you can see, we're going to speak a lot of Microsoft here.

And that is what's going to dictate where we're going. I'm starting with the Microsoft Defender products. And the first thing to know is, what can I do with that product? Not in-depth, just an overview. Learn the namings and what the products cover.

Then learn the primary usage and where to click. After that, colleagues and friends suggested looking deeper into KQL, which is used for hunting. That means a proactive search for anomalies within the vast amount of logs.

So that's it

- Know the Defender products 
- Learn how to use them for monitoring and investigations 
- Learn hunting with KQL

## Resources to learn

### Defender Ninja Show

I started with the Defender Ninja Show. That's a collection of videos based on the Defender for Endpoint Ninja Training (Beginner), which helped me get a rough overview of the MDE capabilities.

### Defender Ninja Training

There is Ninja Training for almost every Defender product out there. And that was next on my list. It consists of small marketing videos, Microsoft Doc articles, and webcasts to let you get to know Defender products. There's usually a beginner, intermediate and expert-level path. But in any way, it's all to get to know the features - nothing in-depth. You can go through this quickly, especially as there is some content where it is more than sufficient to scan over it promptly.

In the end, you will know

- where to click to get to specific areas within the portals 
- understand the basic features of the Defender products 
- know basic KQL to do simple queries via advanced hunting

### SC-900 Training

Microsoft provides some virtual online training sessions via Microsoft Virtual Training Days. Most of them are meant as preparation for the entry-level 900 certifications.

To get a rough overview of the Defender products, how they are working together and what each of the products is covering up, I can recommend the SC-900 preparation material. Virtual Training Day or Microsoft Learn: both have excellent content to get you up and running.

I learned

- the basics of the Defender products 
- how they work together 
- what product is used for what case

### Microsoft Learn

That leads me to the last resource I was using. Microsoft Learn.  
You can find a lot of learning paths of good value for an uprising SOC analyst.

I took the SC-900 and SC-200 paths - well, I read the SC-200 course some months ago out of curiosity and then as preparation for the certification. But I was able to gain a much better understanding of Microsofts security products and their usage.

## What I would have made differently?

Considering the given resources, I would have switched the order in which I consumed the content and probably skipped some points out due to timely reasons

- Start with SC-900 Training 
- Switch over to Ninja Training 
- Skip Ninja Show (maybe later) 
- Earlier hands-on 
- Use Kusto Detective Agent to learn Kusto

## Final thoughts

So, as you can see, there is plenty of material to start immediately. And there is more, like YouTube videos, Pluralsight courses, books, etc…  
For the first four weeks, I stuck with what I could find for free.

Also, start with practical stuff as soon as possible. Set up an M365 dev tenant or use the MDE trial offerings by Microsoft. The sooner you can start playing around the sooner you will be ready to start in production.

But one last resource shall not be forgotten: My colleagues. Through talks, workshops, and just listening when they were chatting, I could get away with a lot of valuable stuff. So keep that in mind and socialize as much as possible.

## References

- [All the Microsoft Ninja Training I Know About - Azure Cloud & AI Domain Blog](https://azurecloudai.blog/2021/05/12/all-the-microsoft-ninja-training-i-know-about/)    
    (https://aka.ms/ninjatraining)
- [Microsoft 365 Defender Virtual Ninja training – Microsoft Adoption](https://adoption.microsoft.com/en-us/ninja-show/)  
    (https://aka.ms/ninja-show)
- [Microsoft Virtual Training Days - Security](https://www.microsoft.com/en-us/trainingdays/security)  
    (https://www.microsoft.com/en-us/trainingdays/security) 
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals - Certifications | Microsoft Learn](https://learn.microsoft.com/en-us/certifications/exams/sc-900)  
    (https://learn.microsoft.com/en-us/certifications/exams/sc-900) 
- [Exam SC-200: Microsoft Security Operations Analyst - Certifications | Microsoft Learn](https://learn.microsoft.com/en-us/certifications/exams/sc-200)  
    (https://learn.microsoft.com/en-us/certifications/exams/sc-200)
- [Kusto Detective Agency](https://detective.kusto.io/)  
    (https://detective.kusto.io)
- [Microsoft Defender for Endpoint Trial](https://aka.ms/mdetrial)  
    (https://aka.ms/mdetrial)
