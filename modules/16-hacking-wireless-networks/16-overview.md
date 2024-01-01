## Hacking Wireless Networks

### Packet Analysis
1. Wireshark
    - Open .cap file
    - 802.11 protocol indicates wireless traffic
    - Association req = SSID + PSK + ARP req

### Crack
1. WEP
   - `aircrack-ng <FILE>.cap`
2. WPA2
   - `aircrack-ng -a2 -b <BSSID (MAC) of target router> -w <WORDLIST> <FILE>.cap`