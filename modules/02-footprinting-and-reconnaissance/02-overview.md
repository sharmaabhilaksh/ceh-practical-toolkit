## Footprinting and Reconnaissance

1. Advanced google search operators
   - `site:` `filetype:` `intitle:` `inurl:` `intext:` `cache:` `link:`
   - `related:` `info:` `allintitle:` `allinurl:` `allintext:` `inanchor:`
2. Reverse image search
3. FTP: searchftps.net
4. IoT: shodan.io
5. website details / domain tools: 
   1. netcraft.com
   2. whois.com
   3. centralops.net
   4. whois.domaintools.com
   5. http://www.kloth.net/services/nslookup.php
   6. DNSdumpster (https://dnsdumpster.com)
   7. DNS Records (https://network-tools.com)
   8. Reverse DNS lookup https://www.yougetsignal.com/tools/web-sites-on-web-server/
   9. DNS Enumeration https://securitytrails.com/
   10. Location: `https://tools.keycdn.com/geo?host=<target IP>`
./6. people search: dnsrecon.py
   1. peekyou.com
   2. spokeo.com
   3. pipl.com
   4. intelius.com
7. ping
   - windows: `ping <destination> -f -l <buffer size> -i <ttl> -n <count> -w <timeout>`
   - linux: `ping <destination> -s <packet size> -t <ttl> -c <count> -W <timeout>`
8. spiders
   1. Web Data Extractor (windows app)
   2. ParseHub (https://www.parsehub.com)
   3. SpiderFoot (https://github.com/smicallef/spiderfoot)
9. copier
   1. HTTrack (windows app)
   2. wget (linux)
   3. Cyotek WebCopy (windows app)
10. Wordlist generator
    - CeWL
      - `cewl <url> -d <depth> -m  <min word len> -w <output file>`
11. Email footprinting
    - eMailTrackerPro (windows app)
    - Infoga (https://github.com/The404Hacking/Infoga)
    - MailTrack (https://mailtrack.io)
12. Network footprinting
    - https://www.arin.net/ OR https://www.iana.org/
      - get the IP range of the target
    - trace route
      - windows: `tracert <domain / IP>`
      - Linux: `traceroute <domain / IP>`
13. OSINT tools
    1. theHarvester
        - `theHarvester -d <domain> -b <source>`
    2. sherlock
        - `python3 sherlock <username>`
    3. photon
        - `python3 photon.py -u <url> -l 3 -t 100`
        - `python3 photon.py -u <url> --clone`
        - `python3 photon.py -u <url> --wayback`
    4. GRecon
        - `python3 grecon.py`
    5. nslookup (windows)
        - `nslookup -type=<type> <domain>`
        - Trust only the authoritative name servers
    6. dnsrecon
        - `./dnsrecon.py -r <ip from>-<ip to>`
        - `./dnsrecon.py -d <domain>`
    7. recon-ng
        - `recon-ng`
          - `modules install all` `modules search`
          - `workspaces create <name>` -> `workspaces list` -> `workspaces select <name>`
          - `db insert domains` `show domains` `show hosts`
          - `modules load <keyword>` -> `modules load <full name>` -> `run`
          - To see options required: `info command`
          - `options set <option name> <value>`
          - Modules:
            - Add hosts for the domain: `recon/domains-hosts/brute_hosts`
            - Resolve IP addresses: `recon/hosts-hosts/reverse_resolve`
            - Reporting: `reporting/*`
            - Extracts the contacts associated with the domain: `recon/domains-contacts/whois_pocs`
            - Extract a list of subdomains and IP addresses associated with the target URL: `recon/domains-hosts/hackertarget`
    8. maltego : provides a library of transforms to discover data from open sources and visualizes that information in a graph format
       - `sudo maltego`
    9. OSRFramework: A collection of scripts to perform Open Source Intelligence tasks
       - `domainfy -n <keyword(s)> -t all`  Fetch all domains and IPs for the keywords 
       - `searchfy` check for the existence of a given user details on different social networking platforms
       - `mailfy` `phonefy` `usufy` `entify`
       - `<XXXXXX>fy -h`
    10. FOCA (Fingerprinting Organizations with Collected Archives) (windows)
        - Document metadata extraction
    11. BillCipher: information gathering tool for a Website or IP address (parrotOS)
        - `python3 billcipher.py`
    12. https://osintframework.com/
        - lists various OSINT tools arranged by category and is shown as an OSINT tree structure
        - (T) - Indicates a link to a tool that must be installed and run locally
        - (D) - Google Dork
        - (R) - Requires registration
        - (M) - Indicates a URL that contains the search term and the URL itself must be edited manually