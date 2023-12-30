## Sniffing

Detect sniffer using nmap: `nmap -script=sniffer-detect <ip address range>`

### Wireshark

#### Display Filters
1. TCP SYN packets: `tcp.flags.syn == 1`
2. Packets from a TCP stream: `tcp.stream eq <n>`
3. HTTP POST requests: `http.request.method == POST`

#### Follow streams
- Choose packet > right click > Follow > [protocol] Stream
- Red is request, Blue is response
- Move to next/previous stream: bottom right corner arrow buttons

#### Finding files
- File > Export Objects > [protocol]
- Sort by content type, host name, or file name
- Save selected items

#### Finding comments
- Select a packet > Open file properties at bottom left > File properties and comments are shown

#### Finding strings
- Ctrl + F > String > Enter string > Find

#### Finding Covert_TCP
- Different stream index for each TCP connection with same source and destination IP addresses and ports

#### Detect DoS / DDoS
- Same destination IP address with same packet type (SYN, ACK, etc.)
- Statistics > Conversations > IPv4/6 > Sort by packets/bytes
- Statistics > I/O Graph : to see when the attack started and ended

#### Detect DHCP starvation
- Huge number of DHCP discover requests
- Click on packet > Expand Ethernet I node > Destination is broadcast MAC address

#### Detect ARP poisoning
- Wireshark > Edit > Preferences > Protocols > ARP > Check "Detect duplicate IP addresses configuration"
- Analyze > Expert Information > Check warning for "Duplicate IP address configured"
- Expand and select any packet in expert information window
- Same packet is selected in the main window
- Go over the details of the packet
- IP1 asking who has IP2 and IP3 and then saying IP2 is at MAC1 and IP3 is at MAC1

#### Password sniffing
- Filter for HTTP POST requests
- Find packet with settings: `packet details :: Narrow (UTF-8 / ASCII) :: String :: <password fild name>`
- Expand HTML form entity body

