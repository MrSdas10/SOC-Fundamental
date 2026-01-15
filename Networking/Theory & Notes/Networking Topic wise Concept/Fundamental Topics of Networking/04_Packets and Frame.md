# 🛡️ Networking Fundamentals for SOC Analysts
_A practical, job-oriented guide for SOC L1 readiness_

---

## 1. Packets and Frames

### Packet (Layer 3 – Network Layer)
**Definition:**  
A packet is a unit of data at the Network Layer that contains **logical addressing (IP addresses)** and payload data.

**Key Components:**
- Source IP Address
- Destination IP Address
- Payload (data)
- TTL, checksum (depending on protocol)

**SOC Relevance:**
- Used in routing, scanning, IP spoofing
- Most IDS/IPS rules inspect packets
- IP-based attacks operate at this level

---

### Frame (Layer 2 – Data Link Layer)
**Definition:**  
A frame is a Layer 2 data unit that **encapsulates a packet** and adds **physical (MAC) addressing** for local delivery.

**Key Components:**
- Source MAC Address
- Destination MAC Address
- Encapsulated packet

**SOC Relevance:**
- ARP spoofing, MAC flooding occur at frame level
- Useful in switch-level attacks
- Seen clearly in Wireshark Layer 2 analysis

---

### Encapsulation
**Definition:**  
Encapsulation is the process of wrapping data with protocol-specific headers as it moves down the network stack.

**Important Rule:**
- Frames change at every hop
- Packets usually remain the same end-to-end

---

## 2. Why Packets Are Used

**Definition:**  
Packets allow large data to be broken into smaller chunks to improve **efficiency, reliability, and congestion control**.

**SOC Insight:**
- Fragmentation can be abused to evade IDS
- Missing or out-of-order packets may indicate attacks

---

## 3. Important IP Packet Headers

| Header | Definition | SOC Importance |
|------|-----------|----------------|
| TTL | Limits packet lifetime | Low TTL = scanning/evasion |
| Checksum | Integrity verification | Detects corruption |
| Source IP | Origin address | Spoofing detection |
| Destination IP | Target address | Asset identification |

---

## 4. TCP/IP Model (Operational Model)

**Definition:**  
The TCP/IP model is the **real-world networking model** used on the internet.

| TCP/IP Layer | Purpose |
|-------------|--------|
| Application | User-facing protocols (HTTP, DNS) |
| Transport | End-to-end delivery (TCP/UDP) |
| Internet | Routing (IP) |
| Network Interface | Physical delivery |

---

## 5. TCP (Transmission Control Protocol)

### TCP Overview
**Definition:**  
TCP is a **connection-oriented**, reliable transport protocol that guarantees data delivery and order.

### Key Characteristics
- Requires connection setup
- Uses acknowledgements
- Performs error correction

---

### TCP Advantages and Disadvantages

**Advantages**
- Guaranteed delivery
- Ordered data
- Error detection

**Disadvantages**
- Slower than UDP
- High overhead
- Vulnerable to SYN flood attacks

---

## 6. TCP Packet Headers (Important Ones)

| Header | Definition |
|------|-----------|
| Source Port | Client-side ephemeral port |
| Destination Port | Server service port |
| Sequence Number | Orders data |
| Acknowledgment Number | Confirms receipt |
| Flags | Control connection state |
| Checksum | Data integrity |
| Data | Actual payload |

---

## 7. TCP Flags (Critical for SOC)

| Flag | Definition |
|----|------------|
| SYN | Initiates connection |
| ACK | Acknowledges packets |
| FIN | Graceful connection close |
| RST | Abrupt reset |
| PSH | Immediate data push |

**SOC Tip:**  
Repeated SYNs without ACKs = possible SYN flood

---

## 8. TCP Three-Way Handshake

**Definition:**  
A three-step process used by TCP to establish a reliable connection.

### Steps:
1. **SYN** – Client requests connection
2. **SYN/ACK** – Server acknowledges
3. **ACK** – Client confirms

**SOC Importance:**
- Half-open connections = DoS
- Unexpected ACKs = spoofing

---

## 9. Sequence Numbers (TCP)

**Definition:**  
Sequence numbers ensure data is delivered **in order** and without duplication.

**SOC Relevance:**
- Session hijacking detection
- Replay attack identification

---

## 10. TCP Connection Termination

### Graceful Close
- FIN → ACK → FIN → ACK

### Abrupt Close
- RST

**SOC Red Flag:**
- Excessive RST packets often indicate scanning or firewall blocks

---

## 11. UDP (User Datagram Protocol)

### UDP Overview
**Definition:**  
UDP is a **connectionless**, stateless transport protocol focused on speed over reliability.

### Characteristics
- No handshake
- No acknowledgments
- No delivery guarantee

---

### UDP Advantages and Disadvantages

**Advantages**
- Very fast
- Low overhead

**Disadvantages**
- Packet loss ignored
- Easily abused for DDoS

**SOC Reality:**
- DNS amplification attacks
- UDP flood attacks

---

## 12. UDP Packet Headers

| Header | Definition |
|------|-----------|
| Source IP | Sender address |
| Destination IP | Receiver address |
| Source Port | Sender port |
| Destination Port | Service port |
| TTL | Packet lifetime |
| Data | Payload |

---

## 13. Ports (Service Identification)

**Definition:**  
Ports are numerical identifiers (0–65535) that map network traffic to specific services.

### Port Ranges

| Range | Meaning |
|-----|--------|
| 0–1024 | Well-known ports |
| 1025–49151 | Registered ports |
| 49152–65535 | Ephemeral ports |

---

## 14. Common SOC-Relevant Ports

| Protocol | Port | SOC Significance |
|--------|------|----------------|
| FTP | 21 | Cleartext credentials |
| SSH | 22 | Brute-force attacks |
| HTTP | 80 | Malware delivery |
| HTTPS | 443 | Encrypted C2 traffic |
| SMB | 445 | Ransomware spread |
| RDP | 3389 | Lateral movement |

**Important Note:**  
Services can run on **non-standard ports** — never trust ports alone.

---

## 15. SOC Analyst Key Takeaways

- Frames = MAC-level (Layer 2)
- Packets = IP-level (Layer 3)
- TCP = reliable but attack-prone
- UDP = fast but abused
- Ports identify services, not security
- Handshake analysis is critical for detection

---

## 16. Important Acronyms (SOC Must-Know)

| Acronym | Meaning |
|-------|--------|
| OSI | Open Systems Interconnection |
| TCP | Transmission Control Protocol |
| UDP | User Datagram Protocol |
| IP | Internet Protocol |
| MAC | Media Access Control |
| TTL | Time To Live |
| SYN | Synchronize |
| ACK | Acknowledgment |
| FIN | Finish |
| RST | Reset |
| ISN | Initial Sequence Number |
| SMB | Server Message Block |
| RDP | Remote Desktop Protocol |
| IDS | Intrusion Detection System |
| DDoS | Distributed Denial of Service |

---


