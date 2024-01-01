## IoT and OT Hacking

### Online footprinting
- Google Hacking DB: https://www.exploit-db.com/google-hacking-database
    - search for "SCADA"
    - Perform google search for `"login" intitle:"*scada login"`
- Shodan: https://www.shodan.io

### Capture and analyze network traffic
- MQTT ports: TCP- 1883, WebSocket- 10443, SSL- 8883
  - Bevywise MQTT Broker and IoT Simulator
- Modbus: 502
- Telnet: 23
- FTP: 21

#### Wireshark for MQTT
- Filter by protocol: `mqtt`
- Types of packets:
  - Publish message: PUBLISH
    - Header Flags: DUP, QoS, RETAIN
  - Publish Received: PUBREC
  - Publish Release: PUBREL
  - Publish Complete: PUBCOMP
  
  Observe `MQ Telemetry Transport Protocol` section for details such as Message Type, Msg Len and Message Identifier.