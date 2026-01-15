# 🌐 Networking Fundamentals for SOC Analysts
_A practical foundation for understanding networks from a defensive security perspective_

---

## 1. What Is a Network?

### Network (General Definition)
**Definition:**  
A network is a collection of **connected entities** that can communicate or share resources with each other.

### Network (Computing Definition)
**Definition:**  
In computing, a network is **two or more devices connected together** to exchange data using defined rules (protocols).

**Examples of Networked Devices:**
- Laptops, desktops, mobile phones
- Servers and routers
- Security cameras, IoT devices
- Traffic lights, industrial sensors

**SOC Importance:**
- Every cyber attack occurs **over a network**
- Without understanding networks, SOC analysis is guesswork

---

## 2. Networks in Everyday Life

Networks exist everywhere:
- Power grids
- Public transport systems
- Postal services
- Weather monitoring systems

**Key Idea:**  
Modern infrastructure depends on networks → attacking networks disrupts real life.

**SOC Perspective:**
- Critical infrastructure attacks (power, transport) rely on network compromise
- SOC teams protect availability and integrity of these systems

---

## 3. Size and Scope of Networks

**Definition:**  
A network can range from:
- **Small**: 2 devices (home PC + router)
- **Huge**: Billions of devices (Internet)

**SOC Insight:**
- Small networks → insider threats
- Large networks → scanning, DDoS, botnets

---

## 4. The Internet (Network of Networks)

### Internet Definition
**Definition:**  
The Internet is a **global public network** formed by interconnecting millions of smaller private networks.

### Key Concept
- Private networks connect to public networks
- Public network = Internet

**SOC Relevance:**
- Internal attacks occur on private networks
- External threats come from public networks

---

## 5. Brief History of the Internet

### ARPANET
**Definition:**  
ARPANET was the first functional computer network, developed in the late 1960s by the U.S. Department of Defense.

### World Wide Web (WWW)
**Definition:**  
The WWW was invented in 1989 by Tim Berners-Lee, enabling information sharing via web pages.

**SOC Insight:**
- Internet was not designed with security in mind
- Most security issues exist because of this

---

## 6. Private Networks vs Public Networks

### Private Network
**Definition:**  
A network used internally (home, office) and **not directly accessible from the Internet**.

### Public Network
**Definition:**  
A network accessible by anyone — typically the Internet.

**SOC Importance:**
- Private network compromise → lateral movement
- Public exposure → external attacks

---

## 7. Device Identification on a Network

### Why Identification Matters
**Definition:**  
For communication to work, devices must be **uniquely identifiable**.

### Two Types of Identification
| Human | Network |
|-----|--------|
| Name | IP Address |
| Fingerprints | MAC Address |

---

## 8. IP Address (Internet Protocol Address)

### IP Address Definition
**Definition:**  
An IP address is a **logical identifier** assigned to a device on a network, either temporarily or permanently.

### IPv4 Structure
- Consists of **4 octets**
- Example: `192.168.1.10`
- Each octet ranges from 0–255

**Important Rule:**
- No two devices can have the same IP in the same network at the same time

---

## 9. Public IP vs Private IP

### Private IP Address
**Definition:**  
Used to identify devices **within a local network**.

Common private ranges:
- 192.168.x.x
- 10.x.x.x
- 172.16–31.x.x

### Public IP Address
**Definition:**  
Used to identify a network or device **on the Internet**, assigned by an ISP.

**SOC Reality:**
- Multiple devices may share one public IP (NAT)
- Attacks appear to come from public IPs

---

## 10. IPv4 Address Exhaustion

### Problem 
IPv4 supports only **~4.3 billion addresses**, which is insufficient for modern Internet usage.

### IPv6 Solution 
IPv6 is the next-generation IP protocol with vastly expanded address space.

**Benefits of IPv6:**
- 2¹²⁸ addresses (practically unlimited)
- Improved routing efficiency
- Better support for modern networks

**SOC Note:**
- Many SOC teams still ignore IPv6 → blind spot

---

## 11. MAC Address (Media Access Control)

### MAC Address Definition
**Definition:**  
A MAC address is a **hardware-based identifier** assigned to a network interface card (NIC) at manufacturing.

### MAC Address Format
- 12 hexadecimal characters
- Example: `a4:c3:f0:85:ac:2d`
- First half → manufacturer
- Second half → unique identifier

---

## 12. MAC Spoofing

### MAC Spoofing Definition
**Definition:**  
MAC spoofing is the act of **impersonating another device’s MAC address**.

### Why It’s Dangerous
- Bypasses MAC-based access controls
- Breaks trust-based security designs

**SOC Example:**
- Firewall allows admin MAC
- Attacker spoofs admin MAC
- Firewall allows attacker

---

## 13. MAC Filtering in Public Wi-Fi

**Definition:**  
MAC filtering allows or restricts devices based on MAC addresses.

**Common Usage:**
- Cafes, hotels, airports
- Paid access per device

**SOC Reality:**
- MAC filtering ≠ security
- Easily bypassed via spoofing

---

## 14. Ping (Network Diagnostic Tool)

### Ping Definition
**Definition:**  
Ping is a network utility that uses **ICMP** to test connectivity and measure latency.

### How Ping Works
1. Sends ICMP Echo Request
2. Receives ICMP Echo Reply
3. Measures round-trip time

---

## 15. ICMP (Internet Control Message Protocol)

**Definition:**  
ICMP is a network-layer protocol used for **diagnostics and error reporting**.

**SOC Importance:**
- ICMP floods → DoS attacks
- Blocked ICMP → troubleshooting difficulty

---

## 16. Using Ping in Practice

### Basic Syntax
```bash
ping <IP address or domain>
