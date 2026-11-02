---
tags: [ "wireshark", "network-analysis", "filters", "blue-team", "pcap" ]
aliases: [ "Packet Analysis", "Display Filters" ]
created: 2025-12-21
---

# 🦈 Wireshark Display Filters

> [!info] Filter Syntax
> Wireshark filters use C-like logic but also support English abbreviations.
> * **eq / ==** : Equal
> * **ne / !=** : Not Equal
> * **and / &&** : Logical AND
> * **or / ||** : Logical OR
> * **not / !** : Logical NOT

## 1. Basic Logical Operators
Combine conditions to isolate specific traffic streams.

- Match TCP port 25 OR any ICMP traffic
- Match standard Windows networking protocols (SMB, NetBIOS, RPC, DNS)
- Complex Exclusion: Exclude specific source AND dest IPs, but keep HTTP
- Subnet Matching (Class C or B)
- Single Host Matching
- Exclusion (Show everything EXCEPT this host)
- Set Membership (Match multiple ranges at once)
- Filter by HTTP Request Method
- Filter by Port Set
- User Agent Matching
- Search for a URL inside HTTP packets
- Search TCP payload for keywords
- Exclude Multicast address

```text title:Logical_Combos
tcp.port eq 25 or icmp

smb || nbns || dcerpc || nbss || dns

ip.src != 192.168.1.5 && ip.dst != 192.168.1.6 && http

ip.src == 192.168.0.0/16 or ip.dst == 192.158.0.0/16

ip.addr == 10.43.54.65

ip.addr != 10.43.54.65
! ( ip.addr == 10.43.54.65 )

ip.addr in {10.0.0.5 .. 10.0.0.9, 192.168.1.1..192.168.1.9}

http.request.method == "POST"
http.request.method in {"HEAD", "GET"}

tcp.port in {80, 443, 8080}

wsp.header.user_agent matches "cldc"

http contains "[https://www.wireshark.org](https://www.wireshark.org)"

tcp.payload contains "GET"
tcp.payload contains "pass"

ip.dst ne 224.1.2.3
not ip.dst or ip.dst ne 224.1.2.3
```
