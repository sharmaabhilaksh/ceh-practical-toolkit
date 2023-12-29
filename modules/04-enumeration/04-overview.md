## Enumeration
It extracts lists of computers, usernames, user groups, ports, OSes, machine names, network resources, and services using various techniques.

Open nmap scripts page: https://nmap.org/nsedoc/scripts/

# Do not try harder, Enumerate Harder


### NetBIOS Enumeration
UDP/137,138 TCP/139
1. `nbtstat -a/-c` `net use`
2. NetBIOS Enumerator (windows app)
3. nmap
   - `nmap -sV -v --script=nbstat <ip>`
   - `nmap -sU -sV -v --script=nbstat <ip>`


### SNMP Enumeration
UDP/161
1. Check that SNMP is running
    - `nmap -sU -p 161 <ip>`
2. snmp-check
   - `snmp-check <ip>`
3. SoftPerfect Network Scanner (windows app)
4. nmap
   - `nmap -sU -p 161 --script=snmp-XXXX <ip>`


### LDAP Enumeration
TCP/389 and TCP/636 (LDAPS)

Domain controllers will show port 389 running the Microsoft Windows AD LDAP service

1. Active Directory Explorer (windows app)
2. ldapsearch
   - `ldapsearch -h <ip> -p <port> -x -s base namingcontexts`
   - `ldapsearch -h [Target IP Address] -x -b “DC=CEH,DC=com”`
   - `ldapsearch -x -h [Target IP Address] -b "DC=CEH,DC=com" "objectclass=*"`
3. nmap scripts


### NFS Enumeration
TCP/2049
1. `nmap -p 2049 <target ip>`
2. use SuperEnum / RPCScan 


### DNS Enumeration
TCP/53
1. Zone Transfer
   1. dig (linux)
      - `dig ns <target domain>`
      - `dig axfr @<name server> <target domain>`
    2. nslookup (windows)
       - `nslookup`
       - `> set querytype=soa`
       - `> <target domain>`
       - `> ls -d <name server>`
2. DNSSEC Zone Walking
   1. DNSRecon (parrot os)
      - `./dnsrecon.py -d [Target domain] -z`
3. using nmap
   1. scripts
      - `nmap -v --script=broadcast-dns-service-discovery [Target Domain]`
      - `nmap -v -T4 -p 53 --script=dns-brute [Target Domain]`
      - `nmap -v --script dns-srv-enum --script-args "dns-srv-enum.domain='[Target Domain]'”`


### SMTP Enumeration
TCP/25
1. `nmap -v -p 25 --script=smtp-**** <target ip>`

### SMB Enumeration
TCP/139,445
1. `nmap -v -p 445 --script=smb-**** <target ip>`
2. `nmap -v -sU -sS --script=smb-**** <target ip>`
3. GUI: `smb://<IP>`

### RDP Enumeration
TCP/3389
1. `nmap -p 3389 --script=rdp-**** <target ip>`

### Tools
1. SuperEnum (parrot os) enumerate all ports
   - create target.txt with ip addresses
   - `./superenum.sh`
   - give target.txt as IP list filename
2. RPCScan (parrot os) enumerate all ports
   - `python3 rpc-scan.py <target IP> --rpc`
3. Netscan tools pro 11 (windows app)
4. global network inventory (windows app)
5. enum4linux (parrot os)