# 🌐 Port Forwarding, Firewalls, VPNs, Routers, Switches & VLANs
_A SOC analyst–oriented guide to exposing, controlling, and securing networks_

---

## 1. What Is Port Forwarding?

### Port Forwarding Definition
**Definition:**  
Port forwarding is a technique that allows **external devices on the Internet** to access a **specific service inside a private network** by mapping a public port to a private IP and port.

### Why Port Forwarding Exists
- Private IP addresses are **not routable on the Internet**
- Without port forwarding, internal services remain **intranet-only**

---

## 2. Port Forwarding – Practical Example

### Scenario
- Internal server: `192.168.1.10`
- Service: Web server on port `80`
- Network access: Only internal devices can reach it

### After Port Forwarding
- Public IP: `82.62.51.70`
- Port mapping: `82.62.51.70:80 → 192.168.1.10:80`
- Result: Anyone on the Internet can access the web server

---

## 3. Port Forwarding vs Firewall (Very Important)

### Port Forwarding
**What it does:**
- Opens a **path** to an internal service
- Configured on the **router**

### Firewall
**What it does:**
- Decides whether traffic is **allowed or denied**
- Inspects packets and connections

### Key Difference
> Port forwarding exposes a service  
> Firewalls control who can reach it

**SOC Reality:**
- Port forwarding without firewall rules = exposed attack surface

---

## 4. What Is a Firewall?

### Firewall Definition
**Definition:**  
A firewall is a security device or software that **monitors, filters, and controls network traffic** based on defined rules.

### Firewall Decision Factors
- Source IP
- Destination IP
- Port number
- Protocol (TCP/UDP)
- Connection state

---

## 5. Firewall Packet Inspection

**Definition:**  
Packet inspection is the process of analyzing packet headers (and sometimes payloads) to make allow/deny decisions.

**SOC Relevance:**
- Firewalls are first-line defense
- Misconfigured rules = breaches
- Firewall logs are critical during incidents

---

## 6. Firewall Categories (Core Types)

### Stateful Firewall

**Definition:**  
A stateful firewall tracks the **entire connection**, not just individual packets.

**Characteristics:**
- Understands TCP handshakes
- Can block an entire host if malicious behavior is detected

**Pros:**
- Smarter decisions
- Better security

**Cons:**
- High resource usage
- Slower under heavy load

**SOC Use Case:**
- Enterprise perimeter firewalls

---

### Stateless Firewall

**Definition:**  
A stateless firewall evaluates **each packet independently** using fixed rules.

**Characteristics:**
- No connection awareness
- Fast and lightweight

**Pros:**
- Handles massive traffic (e.g., DDoS)
- Low resource usage

**Cons:**
- No context awareness
- Rule gaps = blind spots

**SOC Use Case:**
- DDoS mitigation
- Edge filtering

---

## 7. What Is a VPN?

### VPN Definition
**Definition:**  
A VPN (Virtual Private Network) creates an **encrypted tunnel** between devices or networks over the Internet, forming a **private communication path**.

### What a VPN Provides
- Secure communication
- Network extension
- Encrypted data transfer

---

## 8. VPN – Network Example

### Networks
- Network #1: Office A
- Network #2: Office B
- Network #3: VPN tunnel

**Key Idea:**
- Devices in Network #3 behave as if they are on the same private network

**SOC Perspective:**
- VPNs expand the attack surface
- Compromised VPN credentials = internal access

---

## 9. Benefits of VPNs

### Geographical Connectivity
- Connects remote offices
- Enables remote work

### Privacy
- Encrypts traffic
- Protects against sniffing on public Wi-Fi

### Anonymity
- Hides traffic from ISPs
- Depends on VPN provider’s logging policy

**SOC Reality:**
- VPN ≠ full anonymity
- Logs still matter

---

## 10. VPN Use in TryHackMe (Security Design)

**Why VPN Is Used**
- Vulnerable machines are **not exposed to the Internet**
- Traffic appears legitimate to ISPs
- Secure lab environment

**SOC Lesson:**
- Isolation + encryption = safer exposure

---

## 11. VPN Technologies

### PPP (Point-to-Point Protocol)

**Definition:**  
Provides authentication and encryption but **cannot route traffic by itself**.

**Note:**
- Uses certificates and keys
- Legacy technology

---

### PPTP (Point-to-Point Tunneling Protocol)

**Definition:**  
Encapsulates PPP traffic to allow it to travel across networks.

**Pros:**
- Easy to configure
- Wide device support

**Cons:**
- Weak encryption
- Not secure by modern standards

---

### IPSec (Internet Protocol Security)

**Definition:**  
Encrypts IP traffic directly at the network layer.

**Pros:**
- Strong encryption
- Widely supported

**Cons:**
- Complex configuration

**SOC Reality:**
- Common in enterprise VPNs

---

## 12. What Is a Router?

### Router Definition
**Definition:**  
A router is a **Layer 3 device** that connects **different networks** and forwards packets using IP addresses.

### Router Responsibilities
- Routing decisions
- Port forwarding
- Firewall enforcement

**SOC Relevance:**
- Router compromise = full network exposure
- Routing misconfigurations cause outages

---

## 13. Routing Decisions

Routers choose paths based on:
- Shortest path
- Reliability
- Link speed (fiber vs copper)

**SOC Insight:**
- Route hijacking impacts availability and integrity

---

## 14. What Is a Switch?

### Switch Definition
**Definition:**  
A switch is a networking device that **connects multiple devices within the same network** using Ethernet.

### Device Capacity
- Typically 3 to 63 devices

---

## 15. Layer 2 Switch

**Definition:**  
Operates at OSI Layer 2 and forwards **frames using MAC addresses**.

**Responsibilities:**
- MAC address learning
- Frame forwarding

**SOC Relevance:**
- ARP spoofing
- MAC flooding
- VLAN hopping attacks

---

## 16. Layer 3 Switch

**Definition:**  
A Layer 3 switch combines **switching and routing** capabilities.

**Capabilities:**
- Routes packets using IP
- Forwards frames using MAC

**Example IPs:**
- 192.168.1.1
- 192.168.2.1

**SOC Insight:**
- Poor segmentation here = lateral movement

---

## 17. VLAN (Virtual Local Area Network)

### VLAN Definition
**Definition:**  
A VLAN logically separates devices within the same physical network into **isolated virtual networks**.

### Why VLANs Exist
- Security isolation
- Traffic control
- Network organization

---

## 18. VLAN Security Example

### Departments
- Sales
- Accounting

**Result:**
- Both access the Internet
- Cannot communicate with each other

**SOC Benefit:**
- Limits breach impact
- Prevents unauthorized lateral movement

---

## 19. SOC Analyst Key Takeaways

- Port forwarding exposes services
- Firewalls control access
- VPNs extend private networks securely
- Routers connect networks (Layer 3)
- Switches connect devices (Layer 2/3)
- VLANs reduce blast radius

---

## 20. Important Acronyms (SOC Must-Know)

| Acronym | Meaning |
|------|--------|
| VPN | Virtual Private Network |
| NAT | Network Address Translation |
| PPP | Point-to-Point Protocol |
| PPTP | Point-to-Point Tunneling Protocol |
| IPSec | Internet Protocol Security |
| VLAN | Virtual Local Area Network |
| LAN | Local Area Network |
| WAN | Wide Area Network |

---

