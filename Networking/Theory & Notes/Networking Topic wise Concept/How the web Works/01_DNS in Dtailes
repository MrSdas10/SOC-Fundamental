# 🌍 DNS (Domain Name System) – SOC Analyst Master Notes
_A practical, defensive-security guide to how DNS works and how it is abused_

---

## 1. What Is DNS?

### DNS Definition
**Definition:**  
DNS (Domain Name System) is a distributed system that **translates human-readable domain names into IP addresses** so computers can communicate over the Internet.

### Why DNS Exists
- Humans remember names (e.g., `tryhackme.com`)
- Computers use numbers (e.g., `104.26.10.229`)
- DNS acts as the **phonebook of the Internet**

**SOC Importance:**
- Almost every attack involves DNS
- Malware relies on DNS for command-and-control (C2)
- DNS logs are gold for threat detection

---

## 2. IP Addresses (DNS Context)

### IPv4 Address
**Definition:**  
A 32-bit address written as four octets (0–255), e.g. `104.26.10.229`

### IPv6 Address
**Definition:**  
A 128-bit address written in hexadecimal, e.g. `2606:4700:20::681a:be5`

**SOC Insight:**
- DNS resolves both IPv4 and IPv6
- Ignoring IPv6 = blind spot

---

## 3. Domain Hierarchy (How DNS Is Structured)

### Domain Hierarchy Definition
**Definition:**  
DNS uses a **hierarchical structure**, starting from the root and branching downward.

Hierarchy order:
1. Root Domain (`.`)
2. Top-Level Domain (TLD)
3. Second-Level Domain
4. Subdomain(s)

---

## 4. Top-Level Domain (TLD)

### TLD Definition
**Definition:**  
The TLD is the **right-most part** of a domain name.

### Types of TLDs

#### gTLD (Generic Top-Level Domain)
- `.com`, `.org`, `.edu`, `.gov`
- New gTLDs: `.online`, `.club`, `.biz`

#### ccTLD (Country Code Top-Level Domain)
- `.ca` (Canada)
- `.uk`, `.co.uk` (United Kingdom)
- `.in` (India)

**SOC Insight:**
- Attackers often abuse cheap or obscure TLDs
- TLD reputation is useful in threat intelligence

---

## 5. Second-Level Domain (SLD)

### SLD Definition
**Definition:**  
The Second-Level Domain is the **main registered name** under a TLD.

**Example:**
- `tryhackme.com`
- `tryhackme` = SLD
- `.com` = TLD

### Naming Rules
- Max 63 characters
- a–z, 0–9, hyphens
- No starting/ending hyphens

**SOC Relevance:**
- Typosquatting targets SLDs
- Lookalike domains are common phishing tactics

---

## 6. Subdomains

### Subdomain Definition
**Definition:**  
A subdomain is an extension added **to the left of the SLD** to organize services.

**Examples:**
- `admin.tryhackme.com`
- `jupiter.servers.tryhackme.com`

### Characteristics
- Unlimited subdomains
- Total domain length ≤ 253 characters

**SOC Insight:**
- Malware often hides in random subdomains
- Excessive subdomains = DGA or beaconing behavior

---

## 7. DNS Record Types (SOC-Critical)

### A Record
**Definition:**  
Maps a domain name to an **IPv4 address**.

**Example:**  
`tryhackme.com → 104.26.10.229`

---

### AAAA Record
**Definition:**  
Maps a domain name to an **IPv6 address**.

**Example:**  
`tryhackme.com → 2606:4700:20::681a:be5`

---

### CNAME Record
**Definition:**  
Maps a domain name to **another domain name**.

**Example:**  
`store.tryhackme.com → shops.shopify.com`

**SOC Insight:**
- CNAME chains hide real hosting locations
- Used in phishing and CDN abuse

---

### MX Record
**Definition:**  
Specifies **mail servers** responsible for receiving email.

### Key Feature
- Priority value (lower = higher priority)

**SOC Relevance:**
- Email spoofing detection
- Phishing investigations
- Mail infrastructure mapping

---

### TXT Record
**Definition:**  
A flexible text record used to store **arbitrary data**.

### Common Uses
- SPF (email sender validation)
- DKIM / DMARC
- Domain ownership verification

**SOC Insight:**
- Weak SPF = email spoofing
- TXT abuse for malware signaling

---

## 8. What Happens When You Make a DNS Request?

### Step 1: Local Cache
- OS checks if it already knows the answer
- If found → request ends

---

### Step 2: Recursive DNS Server

### Recursive DNS Server Definition
**Definition:**  
A DNS server that **queries other DNS servers on behalf of the client**.

- Usually provided by ISP
- Can be custom (Google, Cloudflare)

**SOC Insight:**
- Recursive DNS logs = detection goldmine

---

### Step 3: Root DNS Servers

### Root Server Definition
**Definition:**  
Root DNS servers direct queries to the **correct TLD server**.

**Example:**
- `.com` queries → `.com` TLD servers

---

### Step 4: TLD DNS Server

### TLD Server Definition
**Definition:**  
Provides the **authoritative nameserver location** for a domain.

---

### Step 5: Authoritative DNS Server

### Authoritative Server Definition
**Definition:**  
The server that **stores the actual DNS records** for a domain.

**Example Nameservers:**
- `kip.ns.cloudflare.com`
- `uma.ns.cloudflare.com`

**SOC Relevance:**
- DNS hijacking targets authoritative servers
- Name server changes = high-risk event

---

### Step 6: Response + Caching

### TTL (Time To Live)

**Definition:**  
TTL is the **time (in seconds)** a DNS record is cached before being refreshed.

**SOC Insight:**
- Low TTL = fast-changing infrastructure (often malicious)
- High TTL = stable, trusted services

---

## 9. DNS Caching (Why It Matters)

### Caching Definition
**Definition:**  
Caching stores DNS responses locally to reduce repeated lookups.

### Benefits
- Faster browsing
- Reduced DNS traffic

### SOC Risks
- DNS cache poisoning
- Persistent malicious records

---

## 10. DNS in Attacks (SOC Reality)

### Common DNS Abuse
- Phishing domains
- DGA (Domain Generation Algorithms)
- DNS tunneling
- Fast-flux hosting

### SOC Detection Clues
- Random-looking domains
- High query frequency
- Unusual TLD usage
- Short TTL values

---

## 11. SOC Analyst Key Takeaways

- DNS translates names to IPs
- DNS is hierarchical and distributed
- Most attacks rely on DNS
- DNS logs are critical for detection
- Subdomains and TTLs reveal attacker behavior

---

## 12. Important Acronyms (SOC Must-Know)

| Acronym | Meaning |
|------|--------|
| DNS | Domain Name System |
| IP | Internet Protocol |
| TLD | Top-Level Domain |
| gTLD | Generic Top-Level Domain |
| ccTLD | Country Code Top-Level Domain |
| SLD | Second-Level Domain |
| TTL | Time To Live |
| MX | Mail Exchange |
| SPF | Sender Policy Framework |
| C2 | Command and Control |

---

