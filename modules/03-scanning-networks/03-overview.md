## Scanning Networks

`namp -sC -sV -p- -T4 <target>`

### Host Discovery
1. nmap / zenmap
   - `nmap -sn -P<type> <ip range>`
2. Angry IP Scanner (windows)
3. netdiscover
   - `netdiscover -r <ip range>`

### Port and service discovery
1. nmap / zenmap
   - `namp -s<type> -p<port> <ip range>`
2. sx network scanner
   - `sx help` `sx <command> help`
3. hping3: network scanning and packet crafting tool
   - `hping3 -p <port> -c <count> <destination ip>`

### OS fingerprinting
1. nmap / zenmap
   - `nmap -O <ip>`
   - `nmap --script smb-os-discovery.nse <ip>`

