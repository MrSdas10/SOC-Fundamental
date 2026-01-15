# 🧱 OSI Model (Open Systems Interconnection) – SOC Analyst Master Notes
_A practical, defensive-security view of how data moves across networks_

---

## 1. What Is the OSI Model?

### OSI Model Definition
**Definition:**  
The OSI (Open Systems Interconnection) model is a **conceptual framework** that defines how data is **sent, received, processed, and understood** across a network.

### Why the OSI Model Exists
- Enables **standardized communication**
- Allows **different vendors and devices** to interoperate
- Provides a **structured way to troubleshoot network issues**

**SOC Importance:**
- Helps isolate **where an attack or failure occurs**
- Maps attacks and detections to specific layers
- Critical for packet analysis and alert triage

---

## 2. Overview of OSI Layers

The OSI model consists of **7 layers**, numbered from **Layer 7 (top)** to **Layer 1 (bottom)**.

| Layer | Name |
|-----|-----|
| 7 | Application |
| 6 | Presentation |
| 5 | Session |
| 4 | Transport |
| 3 | Network |
| 2 | Data Link |
| 1 | Physical |

---

## 3. Layer 1 – Physical Layer

### Physical Layer Definition
**Definition:**  
The Physical layer deals with the **actual hardware and physical transmission of data** using electrical, optical, or radio signals.

### What It Handles
- Cables (Ethernet, fiber)
- Voltages and signals
- Bits (1s and 0s)

### Examples
- Ethernet cables
- Network ports
- Wireless radio signals

**SOC Relevance:**
- Cable damage = network outage
- Physical access = total security failure
- Often ignored but critical in insider threats

---

## 4. Layer 2 – Data Link Layer

### Data Link Layer Definition
**Definition:**  
This layer handles **physical addressing** and prepares data for transmission across the physical medium.

### Key Responsibilities
- MAC addressing
- Frame creation
- Error detection at link level

### Key Component
- **MAC Address** (hardware identifier)

**SOC Relevance:**
- ARP spoofing
- MAC flooding
- Switch-level attacks

---

## 5. Layer 3 – Network Layer

### Network Layer Definition
**Definition:**  
The Network layer is responsible for **logical addressing and routing**, determining how data travels between networks.

### What Happens Here
- IP addressing
- Packet routing
- Path selection

### Routing Protocols (Awareness Only)
- OSPF (Open Shortest Path First)
- RIP (Routing Information Protocol)

### Routing Decisions Based On
- Shortest path
- Reliability
- Link speed (fiber vs copper)

### Devices
- Routers
- Layer 3 switches

**SOC Relevance:**
- IP spoofing
- Routing misconfigurations
- Network-based attacks originate here

---

## 6. Layer 4 – Transport Layer

### Transport Layer Definition
**Definition:**  
The Transport layer controls **end-to-end communication**, deciding how data is delivered between devices.

### Main Protocols
- TCP (Transmission Control Protocol)
- UDP (User Datagram Protocol)

---

### TCP (Transmission Control Protocol)

**Definition:**  
TCP is a **connection-oriented**, reliable protocol that guarantees accurate and ordered data delivery.

#### TCP Advantages
- Data integrity guaranteed
- Ordered delivery
- Flow control

#### TCP Disadvantages
- Slower performance
- High overhead
- Vulnerable to SYN flood attacks

#### TCP Use Cases
- Web browsing
- File transfers
- Emails

**SOC Perspective:**
- SYN floods
- Session hijacking
- TCP flag abuse

---

### UDP (User Datagram Protocol)

**Definition:**  
UDP is a **connectionless**, fast protocol that sends data without delivery guarantees.

#### UDP Advantages
- Very fast
- Low overhead

#### UDP Disadvantages
- No reliability
- Packet loss ignored

#### UDP Use Cases
- Video streaming
- VoIP
- ARP, DHCP

**SOC Perspective:**
- UDP floods
- Amplification attacks
- Harder to inspect reliably

---

## 7. Layer 5 – Session Layer

### Session Layer Definition
**Definition:**  
The Session layer is responsible for **establishing, maintaining, and terminating sessions** between devices.

### Responsibilities
- Session creation
- Session management
- Session termination
- Checkpointing (resuming data transfer)

**Important Note:**
- Sessions are **unique**
- Data does not cross sessions

**SOC Relevance:**
- Session hijacking
- Timeout abuse
- Persistent connections used by attackers

---

## 8. Layer 6 – Presentation Layer

### Presentation Layer Definition
**Definition:**  
The Presentation layer **translates, formats, and encrypts data** so that applications can understand it.

### Key Functions
- Data formatting
- Character encoding
- Encryption and decryption

### Examples
- HTTPS encryption
- Email formatting
- Compression

**SOC Relevance:**
- Encrypted traffic inspection challenges
- TLS/SSL analysis
- Malware hiding in encoded payloads

---

## 9. Layer 7 – Application Layer

### Application Layer Definition
**Definition:**  
The Application layer provides **user-facing network services** and defines how applications interact with the network.

### Common Protocols
- HTTP / HTTPS
- DNS
- FTP
- SMTP
- SSH

### Examples
- Web browsers
- Email clients
- File transfer tools

**SOC Relevance:**
- Most attacks target this layer
- Phishing, malware delivery, C2 traffic
- High-value detection layer

---

## 10. Encapsulation in the OSI Model

### Encapsulation Definition
**Definition:**  
Encapsulation is the process where **each OSI layer adds its own header** to data as it moves down the stack.

### Decapsulation
- Reverse process on receiving device
- Headers removed layer by layer

**SOC Importance:**
- Packet analysis relies on understanding encapsulation
- Identifying malformed or malicious headers

---

## 11. OSI Model – SOC Analyst Mindset

### Why SOC Analysts Use OSI
- Structured troubleshooting
- Attack surface mapping
- Faster root-cause analysis

### Example
- Cable issue → Layer 1
- ARP spoofing → Layer 2
- IP scan → Layer 3
- SYN flood → Layer 4
- Session hijack → Layer 5
- TLS misuse → Layer 6
- Phishing → Layer 7

---

## 12. Key Takeaways for SOC Analysts

- OSI model is a **mental model**, not a protocol
- Every attack maps to one or more layers
- Layer awareness improves detection accuracy
- Packet analysis = OSI knowledge in action

---

## 13. Important Acronyms (SOC Must-Know)

| Acronym | Meaning |
|------|--------|
| OSI | Open Systems Interconnection |
| TCP | Transmission Control Protocol |
| UDP | User Datagram Protocol |
| IP | Internet Protocol |
| MAC | Media Access Control |
| NIC | Network Interface Card |
| DNS | Domain Name System |
| HTTP | HyperText Transfer Protocol |
| HTTPS | HTTP Secure |
| TLS | Transport Layer Security |

---

