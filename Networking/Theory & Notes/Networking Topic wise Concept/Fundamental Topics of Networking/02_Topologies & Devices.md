# 🏠 Local Area Networks (LAN) & Core Networking Concepts for SOC Analysts
_A defensive-security oriented explanation of LAN designs and key network components_

---

## 1. What Is a Network Topology?

### Network Topology
**Definition:**  
A network topology refers to the **physical or logical layout** of how devices are connected within a network.

**Why Topology Matters in SOC:**
- Determines **single points of failure**
- Affects **attack spread**
- Impacts **incident containment and troubleshooting**

---

## 2. Star Topology

### Star Topology Definition
**Definition:**  
A star topology connects all devices **individually to a central device** such as a switch or hub.

### How It Works
- All traffic passes through the central device
- Devices do **not** communicate directly with each other

### Advantages
- Easy to scale (add/remove devices)
- Easier fault isolation
- Better performance than bus/ring

### Disadvantages
- Expensive (more cabling + hardware)
- Central device failure = network outage
- Increased maintenance as network grows

### SOC Perspective
- Switch compromise = entire network visibility risk
- Centralized monitoring is easier
- Ideal topology for enterprise SOC monitoring

---

## 3. Bus Topology

### Bus Topology Definition
**Definition:**  
A bus topology uses a **single backbone cable** that all devices share for communication.

### How It Works
- All devices transmit data on the same cable
- Data travels in both directions

### Advantages
- Cheap to implement
- Minimal cabling
- Simple setup

### Disadvantages
- Severe bottlenecks
- Very hard troubleshooting
- Single cable failure breaks entire network

### SOC Perspective
- Easy traffic sniffing
- No isolation between devices
- Extremely weak from a security standpoint

---

## 4. Ring Topology

### Ring Topology Definition
**Definition:**  
A ring topology connects devices in a **closed loop**, where data travels in one direction.

### How It Works
- Each device forwards data to the next
- A device sends its own data before forwarding others

### Advantages
- Predictable traffic flow
- Fewer collisions
- Easier fault tracing

### Disadvantages
- Inefficient routing
- Single device or cable failure breaks the network
- Poor scalability

### SOC Perspective
- Rare in modern environments
- Easy to detect disruptions
- Poor fault tolerance = availability risk

---

## 5. What Is a Switch?

### Switch Definition
**Definition:**  
A switch is a **Layer 2 networking device** that connects multiple devices and forwards traffic intelligently.

### Key Characteristics
- Maintains a MAC address table
- Sends frames only to intended destination
- Reduces unnecessary traffic

### Port Capacities
- 4, 8, 16, 24, 32, 64 ports

### SOC Importance
- Core visibility point for internal traffic
- Target for ARP spoofing and VLAN hopping
- Switch logs are valuable for investigations

---

## 6. Switches vs Hubs

| Feature | Switch | Hub |
|------|-------|-----|
| Traffic Handling | Intelligent | Broadcasts to all |
| Security | Higher | Very low |
| Performance | Efficient | Poor |
| SOC Visibility | High | Noisy |

---

## 7. Network Redundancy

### Redundancy Definition
**Definition:**  
Redundancy is the practice of creating **multiple paths** for data to travel to prevent downtime.

### SOC Perspective
- Improves availability
- Complicates attack paths
- Essential for enterprise resilience

---

## 8. What Is a Router?

### Router Definition
**Definition:**  
A router is a **Layer 3 device** that connects **different networks** and forwards packets using IP addresses.

### Routing
**Definition:**  
Routing is the process of determining the best path for data to travel between networks.

### SOC Importance
- Controls traffic between subnets
- Enforces security policies
- Common target for misconfiguration attacks

---

## 9. Subnetting

### Subnetting Definition
**Definition:**  
Subnetting is the process of **dividing a large network into smaller networks** (subnets).

### Why Subnetting Exists
- Efficiency
- Security isolation
- Network organization

### Real-World Example
Departments in a business:
- Accounting
- Finance
- HR

Each department → separate subnet

---

## 10. Subnet Mask

### Subnet Mask Definition
**Definition:**  
A subnet mask determines how many hosts a network can contain by dividing network and host portions of an IP address.

### Format
- Same structure as IPv4
- Four octets (0–255)
- Example: `255.255.255.0`

---

## 11. IP Address Usage in Subnets

| Type | Purpose | Example |
|----|--------|--------|
| Network Address | Identifies the subnet | 192.168.1.0 |
| Host Address | Identifies a device | 192.168.1.100 |
| Default Gateway | Routes traffic outside subnet | 192.168.1.254 |

### SOC Importance
- Gateway compromise = subnet compromise
- Host identification critical during incidents

---

## 12. Benefits of Subnetting (Security Focus)

### Efficiency
- Reduces broadcast traffic

### Security
- Limits lateral movement
- Isolates attackers

### Control
- Fine-grained access policies

### SOC Example
Cafe Wi-Fi:
- Employee subnet
- Guest subnet
- Prevents public users accessing POS systems

---

## 13. ARP (Address Resolution Protocol)

### ARP Definition
**Definition:**  
ARP maps **IP addresses to MAC addresses** within a local network.

### Why ARP Exists
- IP works at Layer 3
- Ethernet requires MAC addresses (Layer 2)

---

## 14. How ARP Works

### ARP Cache
**Definition:**  
A local table storing known IP–MAC mappings.

### ARP Messages
| Type | Purpose |
|----|--------|
| ARP Request | “Who owns this IP?” |
| ARP Reply | “I do — here’s my MAC” |

### Process
1. Broadcast ARP Request
2. Device with IP responds
3. Mapping stored in cache

---

## 15. ARP Security Risk

### ARP Spoofing
**Definition:**  
An attack where a device sends **fake ARP replies** to impersonate another device.

### SOC Impact
- Man-in-the-middle attacks
- Credential theft
- Session hijacking

---

## 16. DHCP (Dynamic Host Configuration Protocol)

### DHCP Definition
**Definition:**  
DHCP automatically assigns IP configuration to devices joining a network.

### Why DHCP Is Used
- Eliminates manual IP assignment
- Reduces configuration errors

---

## 17. DHCP Process (DORA)

| Step | Message | Purpose |
|----|--------|--------|
| 1 | Discover | Find DHCP server |
| 2 | Offer | Offer IP address |
| 3 | Request | Request offered IP |
| 4 | ACK | Confirm assignment |

### SOC Relevance
- Rogue DHCP servers = network takeover
- DHCP logs help asset identification

---

## 18. SOC Analyst Key Takeaways

- Topology determines attack impact
- Star topology dominates enterprise networks
- Switches = Layer 2 intelligence
- Routers = Layer 3 control points
- Subnetting limits blast radius
- ARP is essential but dangerous
- DHCP automation can be abused

---

## 19. Important Acronyms (SOC Must-Know)

| Acronym | Meaning |
|------|--------|
| LAN | Local Area Network |
| ARP | Address Resolution Protocol |
| DHCP | Dynamic Host Configuration Protocol |
| IP | Internet Protocol |
| MAC | Media Access Control |
| NIC | Network Interface Card |
| VLAN | Virtual LAN |
| MITM | Man-in-the-Middle |

---

