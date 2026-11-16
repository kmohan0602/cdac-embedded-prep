# Topic: Computer Networks — Complete CCAT Level
# Section B — CS Core

---

## Study Order (follow exactly)

---

### STEP 1: OSI Model (7 Layers)
Read: https://www.geeksforgeeks.org/computer-networks/open-systems-interconnection-model-osi/

Must memorize all 7 layers (top to bottom):
| Layer | Number | Function | Protocols |
|-------|--------|----------|-----------|
| Application | 7 | User interface | HTTP, FTP, SMTP, DNS |
| Presentation | 6 | Encryption, compression | SSL/TLS, JPEG |
| Session | 5 | Session management | NetBIOS, RPC |
| Transport | 4 | End-to-end delivery | TCP, UDP |
| Network | 3 | Routing, IP addressing | IP, ICMP, ARP |
| Data Link | 2 | MAC addressing, framing | Ethernet, WiFi |
| Physical | 1 | Bits over wire | Cables, hubs |

Mnemonic: "All People Seem To Need Data Processing" (top to bottom)

---

### STEP 2: TCP/IP Model
Read: https://www.geeksforgeeks.org/computer-networks/tcp-ip-model/

4-layer model:
| TCP/IP Layer | OSI Equivalent |
|--------------|----------------|
| Application | Application + Presentation + Session (5,6,7) |
| Transport | Transport (4) |
| Internet | Network (3) |
| Network Access | Data Link + Physical (1,2) |

---

### STEP 3: IP Addressing
Read: https://www.geeksforgeeks.org/computer-networks/introduction-of-classful-ip-addressing/
Read: https://www.geeksforgeeks.org/computer-networks/differences-between-ipv4-and-ipv6/

Classful IP addressing:
| Class | Range | Default Subnet Mask | Use |
|-------|-------|---------------------|-----|
| A | 1.0.0.0 – 126.255.255.255 | 255.0.0.0 (/8) | Large networks |
| B | 128.0.0.0 – 191.255.255.255 | 255.255.0.0 (/16) | Medium networks |
| C | 192.0.0.0 – 223.255.255.255 | 255.255.255.0 (/24) | Small networks |
| D | 224.0.0.0 – 239.255.255.255 | — | Multicast |
| E | 240.0.0.0 – 255.255.255.255 | — | Reserved/Research |

Private IP ranges (not routable on internet):
- 10.0.0.0 – 10.255.255.255 (Class A)
- 172.16.0.0 – 172.31.255.255 (Class B)
- 192.168.0.0 – 192.168.255.255 (Class C)

IPv4 vs IPv6:
- IPv4: 32-bit, dotted decimal, ~4 billion addresses
- IPv6: 128-bit, hexadecimal, virtually unlimited addresses

---

### STEP 4: TCP vs UDP
Read: https://www.geeksforgeeks.org/computer-networks/what-is-transmission-control-protocol-tcp/
Read: https://www.geeksforgeeks.org/computer-networks/user-datagram-protocol-udp/

| Feature | TCP | UDP |
|---------|-----|-----|
| Connection | Connection-oriented | Connectionless |
| Reliability | Reliable (ACK, retransmit) | Unreliable |
| Order | In-order delivery | No ordering |
| Speed | Slower | Faster |
| Header size | 20 bytes | 8 bytes |
| Use case | HTTP, FTP, Email | DNS, Video streaming, VoIP |

TCP 3-way handshake:
SYN → SYN-ACK → ACK

---

### STEP 5: Key Protocols
Read: https://www.geeksforgeeks.org/computer-networks/domain-name-system-dns-in-application-layer/
Read: https://www.geeksforgeeks.org/html/what-is-http/

| Protocol | Port | Use |
|----------|------|-----|
| HTTP | 80 | Web pages |
| HTTPS | 443 | Secure web pages |
| FTP | 20/21 | File transfer |
| SMTP | 25 | Send email |
| POP3 | 110 | Receive email |
| DNS | 53 | Domain name to IP |
| DHCP | 67/68 | Dynamic IP assignment |
| SSH | 22 | Secure remote login |
| Telnet | 23 | Unsecure remote login |

---

### STEP 6: Subnetting (Basic)
Read: https://www.geeksforgeeks.org/computer-networks/introduction-to-subnetting/

Must know:
- Subnet mask: determines network vs host part
- /24 = 255.255.255.0 = 254 usable hosts
- /16 = 255.255.0.0 = 65534 usable hosts
- Number of hosts per subnet = 2^(host bits) - 2

---

### STEP 7: Network Devices
Must know differences:
| Device | Layer | Function |
|--------|-------|----------|
| Hub | Layer 1 | Broadcasts to all ports (dumb) |
| Switch | Layer 2 | Forwards based on MAC address |
| Router | Layer 3 | Routes based on IP address |
| Bridge | Layer 2 | Connects two network segments |

---

## Practice Links

IndiaBIX Networking:
https://www.indiabix.com/networking/questions-and-answers/

GFG CN Quiz:
https://www.geeksforgeeks.org/computer-networks/computer-network-quiz-set-1/

---

## Daily Target
- Memorize OSI 7 layers with protocols
- Do 10 CN MCQs on IndiaBIX
- Know port numbers for 8 key protocols
