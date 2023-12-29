## System Hacking

### Maintain access
1. Windows startup folder: `C:\ProgramData\Start Menu\Programs\StartUp`
2. Linux: cronjobs, .bashrc, .bash_profile
3. Rootkits
4. Keyloggers to capture passwords

### Cover tracks
1. Clear logs
   1. Windows
      - Disable auditing
        - `auditpol /get /category:*` to list all auditing categories
        - `auditpol /clear /y` to clear all auditing categories
      - Bat file in CEH tools: `Clear_Event_viewer_Logs`
      - wevtutil
        - run cmd as admin
        - `wevtutil el` to list all logs
        - `wevtutil cl <log name>` to clear system/application/security logs
      - overwrite deleted files
        - `cipher /w:<path>` to overwrite a deleted file
   2. Linux
      - `cat /dev/null > <log file>` to clear a log
2. Disable linux history
   - `export HISTSIZE=0`
3. Clear linux history
   - `history -c` clear history
   - `history -w` clear history for current shell
   - `rm ~/.bash_history` to remove history file
   - `shred ~/.bash_history` to make history file unreadable
   - `shred ~/.bash_history && cat /dev/null > .bash_history && history -c && exit` to clear history and exit