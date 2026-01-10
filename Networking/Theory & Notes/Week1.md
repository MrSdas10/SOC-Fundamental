# Networking Fundamentals – Detailed Notes

This document explains five core networking concepts in depth with practical details and examples.

---

## 1. What is a Network?

### Concept
- A **network** is a group of devices (computers, servers, printers, IoT devices) connected to share resources and exchange data.
- Networks can be:
  - **Wired**: Using Ethernet cables.
  - **Wireless**: Using Wi-Fi or Bluetooth.
- Networks allow communication, collaboration, and centralized resource management.

### Practical Details
- **Home Network Example**: Your laptop, phone, and smart TV connected to a Wi-Fi router.
- **Office Network Example**: Multiple computers connected to a central server and printers.
- **Data Flow**: Information travels in packets from one device to another through switches, routers, and cables.


---

## 2. LAN vs WAN

### LAN (Local Area Network)
- Covers a **small area** (home, office, campus).
- High speed, low latency.
- Example: Wi-Fi in your house or Ethernet in a school lab.
- Devices are usually close together.

### WAN (Wide Area Network)
- Covers a **large geographical area** (cities, countries).
- Slower, more complex.
- Example: The Internet itself is the largest WAN.
- Uses leased telecommunication lines, satellites, or fiber optics.

### Practical Details
- LAN is like your **local neighborhood**: fast, private, easy to manage.
- WAN is like the **highway system**: connects distant places, but more traffic and complexity.
- LAN setup: Router + Switch + Devices.
- WAN setup: ISP backbone + routers + multiple LANs connected.

---

## 3. IP Address & MAC Address

### IP Address (Logical Address)
- Identifies a device on a network.
- Can be **static** (fixed) or **dynamic** (changes).
- Example: `192.168.1.10` (IPv4), `2001:db8::1` (IPv6).
- Used for routing data between devices.

### MAC Address (Physical Address)
- Unique hardware identifier for a device’s network card.
- Permanent, burned into the hardware.
- Example: `00:1A:2B:3C:4D:5E`.
- Used for communication within the same local network.

### Practical Details
- Think of **IP address** as your **house address** (can change if you move).
- Think of **MAC address** as your **fingerprint** (unique and permanent).
- When you send data:
  - IP decides **where** it should go.
  - MAC ensures it reaches the **right device** inside the local network.

---

## 4. TCP vs UDP

### TCP (Transmission Control Protocol)
- **Connection-oriented**: Requires a handshake before communication.
- **Reliable**: Ensures data is delivered correctly (acknowledgements, retransmissions).
- **Slower** but accurate.
- Examples: Web browsing (HTTP/HTTPS), Email (SMTP), File transfer (FTP).

### UDP (User Datagram Protocol)
- **Connectionless**: No handshake, just sends data.
- **Fast** but not reliable (packets may be lost).
- Used for real-time applications.
- Examples: Video streaming, Online gaming, DNS queries.

### Practical Details
- TCP is like a **phone call**: you say hello, the other person responds, then you talk.
- UDP is like a **postcard**: you send it without knowing if it arrives.
- TCP is used when accuracy matters.
- UDP is used when speed matters more than accuracy.

---

## 5. TCP 3-Way Handshake

### Concept
The **3-way handshake** is the process TCP uses to establish a reliable connection between two devices.

### Steps
1. **SYN** → Client sends a request to start communication.
2. **SYN-ACK** → Server acknowledges and responds.
3. **ACK** → Client confirms, connection established.

### Practical Details
- Ensures both client and server are ready to communicate.
- Prevents data loss by confirming both sides are synchronized.
- Example: When you open a website, your browser and the server perform this handshake before any data (like HTML files) is transferred.



# Computer Networking Notes

A structured overview of key networking concepts and security mechanisms.

---

## 📌 Common Networking Ports

Ports are communication endpoints used by protocols and services. Below are the most important ones:

| **Port Number** | **Protocol** | **Service** | **Description** |
|-----------------|--------------|-------------|-----------------|
| 20, 21 | FTP | File Transfer Protocol | 20 for data transfer, 21 for control (login, commands). |
| 22 | SSH | Secure Shell | Encrypted remote login and command execution. |
| 23 | Telnet | Remote Terminal Access | Unencrypted remote login (obsolete, insecure). |
| 25 | SMTP | Simple Mail Transfer Protocol | Sending emails between servers. |
| 53 | DNS | Domain Name System | Resolves domain names to IP addresses. |
| 67, 68 | DHCP | Dynamic Host Configuration Protocol | Assigns IP addresses automatically. |
| 80 | HTTP | Hypertext Transfer Protocol | Standard web traffic (unencrypted). |
| 110 | POP3 | Post Office Protocol v3 | Retrieves emails from mail servers. |
| 143 | IMAP | Internet Message Access Protocol | Accesses emails with advanced features. |
| 443 | HTTPS | Secure HTTP | Encrypted web traffic using SSL/TLS. |
| 445 | SMB | Server Message Block | File/printer sharing in Windows networks. |
| 3389 | RDP | Remote Desktop Protocol | Remote desktop access to Windows systems. |
| 3306 | MySQL | Database Service | Default port for MySQL database connections. |
| 5432 | PostgreSQL | Database Service | Default port for PostgreSQL database connections. |
| 1521 | Oracle DB | Oracle Database | Default port for Oracle database services. |
| 389 | LDAP | Lightweight Directory Access Protocol | Directory services (authentication, user info). |
| 636 | LDAPS | Secure LDAP | Encrypted LDAP communication. |
| 69 | TFTP | Trivial File Transfer Protocol | Lightweight file transfer, often for booting devices. |
| 161, 162 | SNMP | Simple Network Management Protocol | Network monitoring and management. |
| 137–139 | NetBIOS | Windows File Sharing | Legacy Windows networking services. |
| 500 | ISAKMP | VPN (IPSec) | Key exchange for VPN tunnels. |
| 1723 | PPTP | VPN Protocol | Point-to-Point Tunneling Protocol (legacy VPN). |
| 1194 | OpenVPN | VPN Protocol | Secure VPN connections. |

---

## 🌐 HTTP vs HTTPS

### HTTP
- **Port:** 80  
- **Definition:** HyperText Transfer Protocol.  
- **Characteristics:**
  - Stateless, plaintext communication.
  - Vulnerable to interception and attacks.
  - Legacy use, now discouraged.

### HTTPS
- **Port:** 443  
- **Definition:** HyperText Transfer Protocol Secure.  
- **Characteristics:**
  - Uses SSL/TLS for encryption and authentication.
  - Protects against eavesdropping and tampering.
  - Mandatory for modern websites, e-commerce, and banking.
  - Improves SEO and user trust.

| Feature | HTTP | HTTPS |
|---------|------|-------|
| Encryption | ❌ None | ✅ SSL/TLS |
| Security | Vulnerable | Secure |
| Authentication | ❌ No | ✅ Certificate-based |
| Browser Label | "Not Secure" | Padlock icon |
| Use Cases | Legacy sites | Modern secure sites |

---

## 🌍 Domain Name System (DNS)

- **Definition:** DNS is the "phonebook of the Internet," mapping domain names to IP addresses.  
- **Port:** 53 (UDP/TCP).  
- **Process:**
  1. User enters domain name.
  2. Resolver queries root server.
  3. Root directs to TLD server.
  4. TLD directs to authoritative server.
  5. Authoritative server returns IP.
  6. Browser connects to server.

### Common DNS Records
- **A Record:** Domain → IPv4 address.  
- **AAAA Record:** Domain → IPv6 address.  
- **CNAME:** Alias record.  
- **MX:** Mail exchange record.  
- **NS:** Nameserver record.  
- **TXT:** Verification/metadata.  
- **PTR:** Reverse lookup.

### Security
- **DNS Spoofing/Cache Poisoning:** Attackers insert false records.  
- **DNSSEC:** Cryptographic signatures for authenticity.  
- **DoH/DoT:** Encrypt DNS queries for privacy.

---

## 🔒 Firewall, IDS, IPS

### Firewall
- **Role:** Filters traffic based on rules.  
- **Types:** Packet-filtering, Stateful, Application-layer, NGFW.  
- **Purpose:** Gatekeeper controlling access.

### IDS (Intrusion Detection System)
- **Role:** Detects suspicious activity.  
- **Types:** NIDS (network), HIDS (host).  
- **Methods:** Signature-based, anomaly-based.  
- **Purpose:** Security camera—alerts only.

### IPS (Intrusion Prevention System)
- **Role:** Detects and blocks malicious activity.  
- **Placement:** Inline with traffic.  
- **Purpose:** Security guard—actively prevents attacks.  

| Feature | Firewall | IDS | IPS |
|---------|----------|-----|-----|
| Primary Role | Filters traffic | Detects intrusions | Detects & blocks intrusions |
| Action | Allow/deny | Alerts/logs | Prevents/block traffic |
| Placement | Edge/host | Passive monitoring | Inline |
| Response | Rule-based | Notification only | Automated prevention |

---

## ✅ Key Takeaways
- **Ports:** Essential for communication; know the common ones.  
- **HTTP vs HTTPS:** Always prefer HTTPS for security.  
- **DNS:** Critical for name resolution; secure with DNSSEC/DoH.  
- **Firewall/IDS/IPS:** Layered defense—firewall (gatekeeper), IDS (camera), IPS (guard).  

---