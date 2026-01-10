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

