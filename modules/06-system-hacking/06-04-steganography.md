## System Hacking

### Steganography

1. Snow (windows)
   - whitespace steganography
   - Hide data: `snow.exe -C -m <message text> -p <password> <cover file> <output file>`
   - Extract data: `snow.exe -C -p <password> <stego file> <output file>`
   - Size and hash will change
2. Openstego GUI (windows)
   - Hide / extract data in images
   - watermark images
3. StegOnline tool
   - Hide / extract data in images
   - https://stegonline.georgeom.net/upload
3. zsteg (linux)
    - detect stegano-hidden data in PNG & BMP
    - `zsteg <image file>`
4. Timestomp
   - Modify timestamps of files
5. NTFS alternate data steams
   - Open `cmd`
   - create a text file with some data: `notepad visible.txt`
   - create hidden stream text file with secrete data: `notepad visible.txt:hidden.txt`
   - Another way to create: `type hidden.txt > visible.txt:hidden.txt`
   - Size and hash of original file will not change
   - To see: `dir /r`
6. Covert TCP

    Send data over TCP without being detected by IDS/IPS
   - Download `cover_tcp.c`
   - `cc -o cover_tcp cover_tcp.c` on both machines
   - Sender: `./cover_tcp -source <own ip> -source_port <port> -dest <dest ip> -dest_port <port> <message>`
   - Receiver: `./cover_tcp -source <sender's ip> -source_port <own port>` 
   - Sender send file: `./covert_tcp -dest 10.10.1.9 -source 10.10.1.13 -source_port 8888 -dest_port 9999 -file /home/attacker/Desktop/Send/message.txt`
   - Receiver receive file: `./covert_tcp -dest 10.10.1.9 -source 10.10.1.13 -source_port 9999 -dest_port 8888 -server -file /home/ubuntu/Desktop/Receive/receive.txt` 