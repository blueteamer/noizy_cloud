---
title: "A brief introduction to Nmap"
date: "2021-07-16"
tags: 
  - "tools"
---

Nmap is one of the most famous - if not THE most famous - tool for network scanning. Whether you want to know if a specific host in your network is up and running or to check if a machine has specific ports open: Nmap is the tool of choice!

<!--more-->
## Table of content 
{{< toc >}}

Unfortunately, Nmap is so powerful that using it is not quite intuitive. I'll try to provide a brief overview and some common statements which can be used with Nmap.

## How to use Nmap

**Note** | I'm going to use Nmap on my Linux machine. Therefore statements might slightly differ from using Nmap on Mac or Windows.  
Ah yes, that's by the way the good news: Nmap is available on Windows, Linux and Mac. Awesome, isn't it?!

So the syntax for Nmap is pretty straightforward. The challenge is to handle the many switches and options.

```bash
john@kali:~$ nmap -scanType -options your.target.ip.address
```

## The setup of this demo

We are going to use a lab environment where I have several virtual machines up and running. The subnet is defined as 12.0.0.0/24, which means we are looking at any machine between 12.0.0.1 and 12.0.0.254. Our favorite target machine will be at 12.0.0.5.

## Simple ping sweep (discovery scan)

Let's start with a simple "let's-see-what-we-got-here" scan of our network.  
For that, we provide nmap with the information on what subnet we want to scan. -sn tells Nmap to just do a discovery scan by pinging each possible host and making a note if any responds. Not quite sure, but I assume Nmap is doing that using ICMP packages. You might want to double-check that using Wireshark.

```bash
john@kali:~$ nmap -sn 12.0.0.0/24
```

You might encounter a problem, that ICMP packages are heavily monitored by an IDS or even restricted. In such cases, we can try to use a workaround.

## Scanning with arp packages

As most network resolution tasks rely on ARP it's pretty unlikely that ARP is prohibited with a network. At least I have never seen such a configuration.

Well, good for us I think. Cause we can also do a portscan using ARP as the underlying protocol. Nmap requires for this a switch called **\-PR**.

So in this case we're scanning a machine with the IP 12.0.0.5 for any open ports using ARP.

```bash
john@kali:~$ nmap -PR 12.0.0.5
```

## Scan network with non-responsive TCP requests

So, what's next? Ah, right. As a network admin, you're totally aware of the above mentioned situations. And therefore you'll configure your IDS to have an extra focus on ICMP and ARP. That's bad for the guy who's scanning the network.

How can Nmap help us out here? Well, it's sending crappy TCP packages and checks if it receives an "I-cannot-handle-this" response or just nothing - no response at all. Receiving the first case, we can assume there is a service running behind that specific port. Receiving nothing shows us, there's probably nothing.

Advantage: Even better cloaking against IDS.  
Disadvantage: The result might not provide that good quality information as expected.

Here's the statement for this scan:

```bash
john@kali:~$ nmap -PA 12.0.0.0/24 
```

## Scanning a specific range of ports

Scanning all 65535 ports can take some time. Especially if you are doing that for a huge IP range. So, you can tell Nmap actively which ports to scan or also provide a range of ports to be scanned.

Let's have a closer look.

### Scanning for a single port

In this example, we are looking if the machine with IP 12.0.0.5 has SSH enabled and is accessible. Therefore we tell Nmap to specifically look at port 22 with the switch **\-p**.

```bash
john@kali:~$ nmap -p 22 12.0.0.5 
```

**Note |** If you haven't been aware of that SSH typically uses port 22 ;)

### Scan a range of ports

One port is not enough? Nmap can also scan for a range of ports. Here we're scanning our poor 12.0.0.5 machine for any available services in the range of ports 22 to 32.

```bash
john@kali:~$ nmap -p 22-32 12.0.0.5 
```

### Scan the top 100 ports

This is pretty self-explaining.

```bash
john@kali:~$ nmap --top-port 100 12.0.0.5
```

### Explicitly scan all ports

Default is already to scan all ports. But you can of course tell Nmap explicitly to scan all ports. Do that with **\-p-**.

```bash
john@kali:~$ nmap -p- 12.0.0.5
```

## Scan a range of IP addresses

Similar to scanning for a range of ports, we can also define a range of IP addresses.

So we assume having a target somewhere between 12.0.0.100 and 12.0.0.160 and we want to see if SSH is enabled (port 22).

```bash
john@kali:~$ nmap -p 22 12.0.0.100-160
```

**Note |** This includes 100 and 160 in the scan.

## What's next?

We've learned the first basics of using Nmap to discover hosts and ports within a network. We also learned that we have different ways in doing a scan. Some are easy to do, but might bring the attention from SecGuys to your place. Others are less aggressive but also have some downsides.

In the end, we can say Nmap is an awesome tool with a whole bunch of capabilities. Covering all would take too long in one blog post. But fortunately, others already did great documentation. And though it's not the most exciting piece of paper, it's definitely worth to be read.

## Reference

\[1\] [Nmap official documenation](https://nmap.org/docs.html) (2021-07-11)
