## Denial of Service

## Detect
1. [Using wireshark](../08-sniffing/08-overview.md#detect-dos--ddos)
2. Using Anti DDoS Guardian
    - Monitor traffic to identify suspicious IP addresses
    - Double click to see high number of packets being sent
    - Block the IP address

### Other attack types:
- Fragmentation:
  - Ping of death: packet size > 65535
  - Teardrop: overlapping fragments
- Slowloris: 
  - HTTP GET request with partial header
  - HTTP POST request with partial body