---
title: "Starting as a SOC analyst with Microsoft Defender for Endpoint | Ninja Training Intermediate and Expert"
date: "2022-09-20"
tags: 
  - "becoming-a-soc-analyst"
  - "mde"
draft: true
---

Second week in becoming a SOC analyst with Microsoft Defender for Endpoint. Let's do a quick recap.

## Content

- [**Resources**](#Resources)
    - [MDE Ninja Training | Intermediate](#MDE-Ninja-Training-|-Intermediate)
    - [MDE Ninja Training | Expert](#MDE-Ninja-Training-|-Expert)
- [**What I've learned in this week**](#What-I've-learned-in-this-week)
    - [Inside of MDE](#Inside-of-MDE)
    - [Advanced hunting with KQL](#Advanced-hunting-with-KQL)
    - [Skills expected](#Skills-expected)
- [**Next steps**](#Next-steps)

## Resources

**Info |** By the way, until now (Sept. 2022) there is no Ninja Show equivalent for the intermediate section of the MDE Ninja Training. So looking forward for the next seasons.

### MDE Ninja Training | Intermediate

- [Security Operations Intermediate](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281212)
    - [Module 1 Architecture](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281213)
    - [Module 2 Threat and vulnerability management](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281214)
    - [Module 3 Next generation protection](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281215)
    - [Module 4 Advanced hunting](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281216)
    - [Module 5 Automated investigation and remediation](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281217)
    - [Module 6 Threat analytics](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281218)
    - [Module 7 Unified indicators of compromise (IOCs)](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281219)
    - [Module 8 Evaluation lab](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281220)
    - [Module 9 Community (blogs, webinars, GitHub)](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281221)

### MDE Ninja Training | Expert

The last part of the Ninja Training for Security Operations.

- [Security Operations Expert](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281222)
    - [Module 1 Responding to threats](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281223)
    - [Module 2 Alert handling](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281224)
    - [Module 3 File analysis](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281225)
    - [Module 4 Advance hunting](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281226)
    - [Module 5 Unified indicators of compromise IOCs](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281227)
    - [Module 6 Custom reporting](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281228)
    - [Module 7 Community (blogs, webinars, GitHub)](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/become-a-microsoft-defender-for-endpoint-ninja/ba-p/1515647#_Toc45281229)

## What I've learned in this week

This time I went a bit faster through the Intermediate and expert part of the Ninja Training. Both together took me around 3 days, whereas the videos about KQL took most of the time. I really wanted to understand every detail of it.

### Inside of MDE

- **Monitoring Incidents with MDE:** Maybe the most common purpose of Defender for Endpoint. MDE is capable of doing a lot of investigations and remediation on its own by leveraging playbooks provided by Microsoft. These are running in the background without any interaction of a soc analyst or user. Nevertheless, those alerts are still mentioned in the list of new alerts. And a soc analyst will go through each single one of them - already remediated or not. If the analyst decides everything is fine, the alert/incident can be closed with a proper documentation for the client.
- **Threat and vulnerability Management (TVM):** Leveraging the Threat Intelligence stream provided by Microsoft, this feature gives you a list of all software used on the managed devices and any threat (-level) based on known CVEs. The soc analyst can also take recommendations for improvements and implement them for the client.
- **Advanced hunting:** Using Kusto Query Language (KQL) an analyst can explore the vast amount of data search for flaws and anomalies within all the logs. For special purposes you can use a KQL query and save it as Custom Detection rule, which can also raise an alert on specific conditions.
- **Attack Surface Reduction rules (ASR rules):** These rules - hardening the endpoint - are used to control behavior on the endpoints itself like prohibiting execution of files or makros.

**Info |** This is not everything that can be done with MDE or where MDE is interconnected with, but the stuff that stick to my mind. It will probably take some additional months to get a proficient knowledge of this tool.

### Advanced hunting with KQL

Advanced hunting with KQL get's an extra mention, as I'm really excited about this feature. Proactively searching the logs for threats, IOCs and stuff. That's really cool and I'm sure, that's something with fun potential - at least for me. ;)

Also, my colleague gave me a real life use case where I could improve my theoretical knowledge with some practical experience - and that was really fun to see that the query might bring some added value for the team.

### Skills expected

While reading what you can do with Defender for Endpoint and how things work, I realized it is of advantage when you have

- **System Administration skills:** As it is part of investigations on endpoints, it is very much of advantage to have a proper understanding of OS, processes and common files, usual behavior on devices and network thingies. Having this skill set makes it probably easier to understand what's going on, what's suspicious and what's normal behavior.
- **Data analysis skills:** As cloud solutions and the security detection behind that produce a lot of data and logfiles, it's important to know how to navigate within the huge amount of data. Defender and Sentinel are using KQL for that - a SQL-ish query language that you can use to get the data you need. Proper understanding of joins, grouping and data visualization is a big plus.
- **Developer skills:** Automate stuff by scripting, analysis of apps, just understand why software is doing what it's doing... all these points will make your life a bit easier. You don't have to be the big cheese python-xtrem-programming-tdd-scrum-nerd. But basic understanding will not be of harm for this job.
- **The cool:** Sort of a soft-skill, if you ask me, but never-the-less important. It no help if you lose your temper as soon as something is not working as expected. Especially in case a serious alert pops up. Remain calm, check what's going on, ask for help if you don't make any progress.

As you can see, it's actually a potpourri of skills you should call your own to have an easier live. Know the basics of everything a bit and then pick a topic to specialize in, later.

Well, at least that's my plan.

## Next steps

As a next step, I'll try to get some more practical experience. Many of my colleagues already offered me to have a look over their shoulders while they are doing our day-to-day tasks. Can't stress enough how entitled I am to be part of this team.

- Practical experience with Incident/Alert Handling
- Improve knowledge KQL with real life use cases
- Basics: Cyber Kill Chain and Mitre Att&ck Framework
