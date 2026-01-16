# 🌐 HTTP & HTTPS – SOC Analyst Master Notes
_A practical, defensive-security guide to web traffic, attacks, and investigation_

---

## 1. What Is HTTP?

### HTTP Definition
**Definition:**  
HTTP (HyperText Transfer Protocol) is an **application-layer protocol** used for transferring web data between a client (browser) and a web server.

### What HTTP Is Used For
- Loading web pages (HTML)
- Transferring images, videos, scripts
- Communicating with web applications

**SOC Reality:**
- Most attacks start over HTTP
- HTTP traffic is human-readable (plaintext)
- Easy to intercept, modify, and abuse

---

## 2. What Is HTTPS?

### HTTPS Definition
**Definition:**  
HTTPS (HyperText Transfer Protocol Secure) is HTTP **encrypted using TLS/SSL**, providing confidentiality, integrity, and authentication.

### What HTTPS Protects
- Prevents traffic sniffing
- Prevents data tampering
- Verifies the server’s identity

**SOC Insight:**
- HTTPS hides content, not behavior
- Encrypted traffic still leaks metadata (domains, IPs, timing)

---

## 3. HTTP vs HTTPS (SOC View)

| Feature | HTTP | HTTPS |
|------|------|-------|
| Encryption | ❌ No | ✅ Yes |
| Confidentiality | ❌ None | ✅ Strong |
| Integrity | ❌ None | ✅ Guaranteed |
| MITM Protection | ❌ No | ✅ Yes |
| SOC Visibility | High | Limited (metadata only) |

---

## 4. What Is a URL?

### URL Definition
**Definition:**  
A URL (Uniform Resource Locator) is an **instruction that tells the browser how and where to access a resource** on the Internet.

---

## 5. URL Components (Very Important)

Example:
```

[http://user:password@tryhackme.com:80/view-room?id=1#task3]

````

### URL Breakdown

| Component | Description |
|-------|------------|
| Scheme | Protocol to use (HTTP, HTTPS, FTP) |
| User | Username (rare, insecure) |
| Password | Password (deprecated, dangerous) |
| Host | Domain name or IP address |
| Port | Network port (80, 443, custom) |
| Path | Resource location |
| Query String | Parameters sent to server |
| Fragment | Page reference (client-side only) |

**SOC Insight:**
- Query strings often contain sensitive data
- Credentials in URLs = critical security issue

---

## 6. Making an HTTP Request

### Minimal Request
```http
GET / HTTP/1.1
````

### Full Example Request

```http
GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: https://tryhackme.com/
```

---

### HTTP Request Breakdown

| Line           | Purpose                            |
| -------------- | ---------------------------------- |
| GET / HTTP/1.1 | Method, resource, protocol version |
| Host           | Specifies which site to access     |
| User-Agent     | Browser and OS information         |
| Referer        | Previous page                      |
| Blank line     | Marks end of request               |

**SOC Insight:**

* User-Agent spoofing is common
* Referer leaks internal URLs
* Missing headers = automation or malware

---

## 7. HTTP Response Structure

### Example Response

```http
HTTP/1.1 200 OK
Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:03 GMT
Content-Type: text/html
Content-Length: 98

<html>...</html>
```

---

### HTTP Response Breakdown

| Line            | Meaning                |
| --------------- | ---------------------- |
| HTTP/1.1 200 OK | Protocol + status code |
| Server          | Web server software    |
| Date            | Server time            |
| Content-Type    | Data type              |
| Content-Length  | Size of response       |
| Blank line      | End of headers         |
| Body            | Requested content      |

**SOC Insight:**

* Server header reveals technology stack
* Content-Type mismatch = exploit attempt

---

## 8. HTTP Methods (Attack Surface)

### GET

**Definition:**
Retrieves data from the server.

**SOC Risk:**
Sensitive data in URLs, logs, browser history

---

### POST

**Definition:**
Submits data to the server.

**SOC Risk:**
Credential theft, injection attacks

---

### PUT

**Definition:**
Updates existing data.

**SOC Risk:**
Unauthorized data modification

---

### DELETE

**Definition:**
Deletes data.

**SOC Risk:**
Account or data destruction if misconfigured

---

## 9. HTTP Status Codes

### Status Code Ranges

| Range   | Meaning       |
| ------- | ------------- |
| 100–199 | Informational |
| 200–299 | Success       |
| 300–399 | Redirection   |
| 400–499 | Client Errors |
| 500–599 | Server Errors |

---

## 10. Common HTTP Status Codes (SOC Must-Know)

| Code | Meaning             | SOC Insight          |
| ---- | ------------------- | -------------------- |
| 200  | OK                  | Normal               |
| 201  | Created             | Resource creation    |
| 301  | Moved Permanently   | SEO / redirect abuse |
| 302  | Found               | Temporary redirect   |
| 400  | Bad Request         | Malformed input      |
| 401  | Unauthorized        | Auth required        |
| 403  | Forbidden           | Access control       |
| 404  | Not Found           | Enumeration          |
| 405  | Method Not Allowed  | Misuse attempt       |
| 500  | Internal Error      | Server failure       |
| 503  | Service Unavailable | DoS or outage        |

---

## 11. HTTP Headers (Critical for SOC)

### Request Headers

| Header          | Purpose               |
| --------------- | --------------------- |
| Host            | Identifies website    |
| User-Agent      | Client fingerprinting |
| Content-Length  | Data size             |
| Accept-Encoding | Compression methods   |
| Cookie          | Session tracking      |

---

### Response Headers

| Header           | Purpose                |
| ---------------- | ---------------------- |
| Set-Cookie       | Creates client cookies |
| Cache-Control    | Caching behavior       |
| Content-Type     | Data format            |
| Content-Encoding | Compression type       |

**SOC Insight:**

* Header manipulation = common attack technique
* Cookie headers = session hijacking target

---

## 12. Cookies

### Cookie Definition

**Definition:**
Cookies are **small pieces of data stored on the client** to maintain state in a stateless protocol.

### Why Cookies Exist

* HTTP does not remember users
* Cookies store session identifiers

---

### Cookie Security Reality

* Cookies usually store **tokens**, not passwords
* If stolen → session takeover
* Insecure cookies = account compromise

**SOC Detection:**

* Reused cookies
* Cookies sent over HTTP
* Missing security flags

---

## 13. Viewing Cookies (Investigation Skill)

### How to View Cookies

* Browser Developer Tools
* Application tab → Cookies
* Network tab → Request headers

**SOC Use Case:**

* Investigate authentication issues
* Validate session handling
* Detect insecure configurations

---

## 14. HTTP(S) in Attacks (SOC Reality)

### Common Abuse

* Credential harvesting
* Malware delivery
* Command-and-control over HTTPS
* Web application attacks

### SOC Clues

* Suspicious User-Agents
* Repeated 401/403 responses
* Abnormal status code patterns
* Unusual methods (PUT, DELETE)

---

## 15. SOC Analyst Key Takeaways

* HTTP is plaintext and dangerous
* HTTPS encrypts content, not intent
* URLs leak sensitive data
* Headers reveal client and server behavior
* Cookies are authentication gold

---

## 16. Important Acronyms (SOC Must-Know)

| Acronym | Meaning                     |
| ------- | --------------------------- |
| HTTP    | HyperText Transfer Protocol |
| HTTPS   | HTTP Secure                 |
| URL     | Uniform Resource Locator    |
| TLS     | Transport Layer Security    |
| SSL     | Secure Sockets Layer        |
| C2      | Command and Control         |
| MITM    | Man-in-the-Middle           |
| GUI     | Graphical User Interface    |

---
