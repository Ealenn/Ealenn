---
title: "DNS sinkhole, between Privacy and AdBlocker, configuration and feedback"
date: 2021-01-02T20:00:00+01:00
description: Protect your devices from unwanted content and guard your privacy with a DNS sinkhole, without installing any client-side software.
menu:
  sidebar:
    name: DNS Sinkhole
    identifier: dns-sinkhole
    parent: raspberry
    weight: 10
---

DNS sinkhole technology provides an effective shield against unwanted online content without the hassle of installing client-side software. 
In this article, we'll explore how DNS sinkholes work, their advantages, and two leading solutions: Pi-Hole and AdGuard.

## Introduction

### Filtering

Filtering DNS queries plays a role in bolstering online security and safeguarding our digital privacy. 

By intercepting and scrutinizing DNS requests, we can proactively block potential threats and security menaces before they even reach our devices. This not only shields us from malicious websites and phishing attempts but also adds an extra layer of defense against cyberattacks like malware distribution and ransomware. 

Furthermore, DNS filtering empowers individuals to take control of their online privacy by thwarting the data-hungry scripts employed by big companies to harvest and monetize our personal information. By blocking these privacy sniffers, we can reduce the risk of our data being exploited for targeted advertising or other intrusive purposes. 

Last but not least, DNS filtering is a potent tool for eliminating the incessant barrage of ads that clutter our browsing experience. It not only enhances our online efficiency but also minimizes the exposure to potentially deceptive or harmful advertisements. 

In essence, DNS filtering serves as a versatile guardian of our digital world, fortifying our security, preserving our privacy, and decluttering our online landscape.

### DNS Queries

DNS (Domain Name System) queries play a crucial role in converting web addresses (e.g., duckduckgo.com) into IP addresses that your devices can understand (e.g., 40.114.177.156).

{{<img src="/posts/raspberry/dns-sinkhole/diagram/dns-query.png" height="342" width="246" align="center" >}}

The DNS sinkhole operates as an intermediary between your DNS server and client devices, such as computers, TVs, tablets, and phones. Depending on your DNS sinkhole's configuration, it can either accept or deny requests based on a DNS Sinkhole List.
DNS sinkholes categorize queries into two lists: the allowlist and blocklist.

{{< split 6 6 >}}
![](./diagram/allow-list.png)
<hr>
---
![](./diagram/block-list.png)
{{< /split >}}

> ![](./diagram/app.png) DNS-Sinkhole
> ![](./diagram/configuration-file.png) DNS-Sinkhole List 
> ![](./diagram/dns.png) DNS Server 
> ![](./diagram/arrow-blue.png) DNS-Sinkhole Request/Response
> ![](./diagram/arrow-red.png) DNS Request/Response

#### DNS-Sinkhole List

Here's a sample of DNS-Sinkhole Lists:

```sh
amptrack.dailymail.co.uk #DailyMail Tracker
analytics.gandi.net #Gandi
analytics.yahoo.com #Yahoo
arc.msn.com #Microsoft
areyouahuman.com #Are You A Human
atdmt.com #Facebook
#...
```

By default, DNS-Sinkhole employs its own list, but you can easily add more from sources like GitHub. I created my own lists and I share them on GitHub at [Ealenn/AdGuard-Home-List](https://github.com/Ealenn/AdGuard-Home-List), which is suitable for corporate use and combines popular lists.

To configure AdGuard Home, use its main menu to add one blocklist and one allowlist:

BlockList :
- https://raw.githubusercontent.com/Ealenn/AdGuard-Home-List/gh-pages/AdGuard-Home-List.Block.txt

AllowList :
- https://raw.githubusercontent.com/Ealenn/AdGuard-Home-List/gh-pages/AdGuard-Home-List.Allow.txt

### DNS Server Redundancy

Another advantage of DNS sinkholes is the availability of multiple DNS servers.

If one DNS server becomes inaccessible, your system can automatically switch to another. This redundancy is crucial in scenarios like DDoS attacks, as seen [in the 2016 Dyn cyberattack](https://en.wikipedia.org/wiki/2016_Dyn_cyberattack) and the 2018 French internet service provider Free DNS breakdown.

{{< img src="/posts/raspberry/dns-sinkhole/diagram/multiple-dns.png" height="352" width="437" align="center" >}}

Personally I use :

- Cloudflare, the fastest DNS resolver on Earth
- Google
- Cisco Open DNS

```sh
# AdGuard
94.140.14.14
94.140.15.15
https://dns.adguard.com/dns-query
tls://dns.adguard.com
# Cloudflare DNS
1.1.1.1
1.0.0.1
https://dns.cloudflare.com/dns-query
tls://1.1.1.1
# Google
8.8.8.8
8.8.4.4
https://dns.google/dns-query
tls://dns.google
# Cisco OpenDNS
208.67.222.222
208.67.220.220
https://doh.opendns.com/dns-query
# Dyn DNS
216.146.35.35
216.146.36.36
```

## Concretely

### Open Source Leaders

#### Pi-Hole

![GitHub last commit](https://img.shields.io/github/last-commit/pi-hole/pi-hole?style=flat-square)
![GitHub Repo stars](https://img.shields.io/github/stars/pi-hole/pi-hole?style=flat-square)
![Docker Pulls](https://img.shields.io/docker/pulls/pihole/pihole?style=flat-square)

- Maintained by developers from the US, Canada, England, Germany, and Australia
- Boasts a sizable community for easy support
- Blocklists and allowlists are regularly updated and maintained by the developers

#### AdGuard

![GitHub last commit](https://img.shields.io/github/last-commit/AdguardTeam/AdGuardHome?style=flat-square)
![GitHub Repo stars](https://img.shields.io/github/stars/AdguardTeam/AdGuardHome?style=flat-square)
![Docker Pulls](https://img.shields.io/docker/pulls/adguard/adguardhome?style=flat-square)

- Most developers are located in Moscow, Russia
- Cleaner interface compared to Pi-Hole
- Utilizes fewer system resources (RAM)
- Supports DNS-Over-HTTPS

### Web Interface

Both Pi-Hole and AdGuard offer similar-looking main dashboards accessed via a web browser.
These dashboards provide useful statistics and graphs regarding the effectiveness of the ad blockers.

{{< split 6 6 >}}
### Pi-Hole
![](./pi-hole.png)
---
### AdGuard
![](./adguard.png)
{{< /split >}}

### Installation

{{< alert type="warning" >}}
**Note**: Ensure your router (or DHCP server) assigns a static IP address to your DNS sinkhole.
{{< /alert >}}

{{< split 6 6 >}}
#### Pi-Hole

For more information, refer to the official Pi-Hole documentation [here](https://docs.pi-hole.net/).

``` yml
version: "3"
services:
  pihole:
    container_name: pihole
    image: pihole/pihole
    ports:
      - "53:53/tcp"
      - "53:53/udp"
      - "67:67/udp"
      - "8000:80/tcp"
      - "4443:443/tcp"
    environment:
      TZ: 'Europe/Paris'
      WEBPASSWORD: 'Password used for Web Administration'
      ServerIP: 'IP of Pi-Hole'
    volumes:
      - './etc-pihole/:/etc/pihole/'
      - './etc-dnsmasq.d/:/etc/dnsmasq.d/'
    dns:
      - 1.1.1.1
      - 8.8.8.8
      - 8.8.4.4
    cap_add:
      - NET_ADMIN
    restart: unless-stopped
```
---
#### AdGuard

For more information, refer to the official AdGuard Home documentation [here](https://kb.adguard.com/en/home/overview).

``` yml
version: "3" 
services:
  adguard:
    container_name: adguardhome
    image: adguard/adguardhome
    ports:
      - "53:53/tcp"
      - "53:53/udp"
      - "67:67/udp"
      - "68:68/tcp"
      - "68:68/udp"
      - "8000:80/tcp"
      - "4443:443/tcp"
      - "853:853/tcp"
      - "3000:3000/tcp"
    volumes:
      - ./workdir:/opt/adguardhome/work
      - ./confdir:/opt/adguardhome/conf
    dns:
      - 1.1.1.1
      - 8.8.8.8
      - 8.8.4.4
    cap_add:
      - NET_ADMIN
    restart: unless-stopped
```
{{< /split >}}

---

You have two options for implementation:
- use it as a DHCP server for automatic configuration 
- or manually configure the DNS server on your devices to use your Raspberry Pi's IP address.

> **Personally, I've configured my devices to use the DNS server.**

## Feedback

After using Pi-Hole for six months and AdGuard for another six months, both solutions proved nearly identical.
However, AdGuard Home offers a more appealing interface and easy DNS-Over-HTTPS setup.

It's important to note that DNS sinkholes can't block all ads or junk content, as some domains serve multiple purposes. For now, domains like Facebook, YouTube, or Google can't be entirely blocked without causing functionality issues. 

Nevertheless, DNS sinkholes can effectively block a substantial portion of unwanted content. On my network, with AdGuard, approximately 10-20 percent of DNS requests are refused, effectively blocking ads and enhancing privacy.

{{< split 6 6 >}}
Ads
- adservice.google.com
- ads.yahoo.com
- ...
---
Privacy
- metrics.***.com
- app-measurement.com
- analytics.***.com
- privatestats.whatsapp.net
- ...
{{< /split >}}
