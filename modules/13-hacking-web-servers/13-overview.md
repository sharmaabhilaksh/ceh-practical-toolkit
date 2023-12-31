## Hacking Web Servers

### Information Gathering
1. nmap scripts
   - Enumerate server info, pages, directories, and files
     - `nmap -sV --script=http-enum <ip/domain>`
   - Enumerate hostnames (other websites on the same server)
     - `nmap --script hostmap-bfk -script-args hostmap-bfk.prefix=hostmap- <ip/domain>`
   - Check HTTP trace is enabled
     - `nmap --script http-trace -d <ip/domain>`
   - Check if web application firewall is in place
     - `nmap --script http-waf-detect <ip/domain>`
2. NetCat or Telnet
    - `telnet <ip/domain> <port>` or `nc -vv <ip/domain> <port>`
    - `GET / HTTP/1.0` then enter twice
    - Observe header values for server and version
3. Ghost eye
    - `pip3 install -r requirements.txt`
    - `python3 ghosteye.py`
4. skipfish
    - `skipfish -o <output directory> <ip/domain>`
5. Others: httprecon, ID Serve, Uniscan

### Attack
1. Crack FTP credentials
   - check if port 21 is open
   - check FTP server is hosted: `ftp <ip/domain>`
   - Dictionary attack using THC Hydra
     - Copy wordlist from CEH Tools > module 13
     - `hydra -L <.../wordlist/Usernames.txt> -P <.../wordlist/Passwords.txt> ftp://<ip/domain>:<port>`
     - use credentials to login to FTP server