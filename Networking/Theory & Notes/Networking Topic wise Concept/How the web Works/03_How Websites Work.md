# 🌐 Web Fundamentals (HTML, JavaScript & Client-Side Security)
_A SOC Analyst–oriented introduction to how websites work and how they fail_

---

## 1. How Websites Work (Big Picture)

### Website Communication Flow
**Definition:**  
When you visit a website, your **browser (client)** sends a request to a **web server**, and the server responds with data that the browser renders as a web page.

### Web Server
**Definition:**  
A web server is a dedicated computer that:
- Receives requests (HTTP/HTTPS)
- Processes them
- Sends back responses (HTML, images, scripts, etc.)

**SOC Reality:**
- Attacks target servers, not browsers
- Logs from web servers are critical during investigations

---

## 2. Core Components of a Website

Websites are built using **two major components**:

### Front End (Client-Side)
**Definition:**  
The front end is everything **rendered and executed in the browser**.

Technologies:
- **HTML** – structure
- **CSS** – appearance
- **JavaScript** – behavior & interactivity

### Back End (Server-Side)
**Definition:**  
The back end is the server logic that:
- Processes requests
- Handles authentication
- Interacts with databases
- Returns responses

**SOC Insight:**
- Front end leaks information
- Back end controls access

---

## 3. What Is HTML?

### HTML Definition
**Definition:**  
HTML (HyperText Markup Language) is the **standard language used to structure web pages**.

### HTML Elements (Tags)
**Definition:**  
Elements (tags) tell the browser **what content is and how to display it**.

Examples:
- `<h1>` – heading
- `<p>` – paragraph
- `<button>` – button
- `<img>` – image

---

## 4. Basic HTML Document Structure

### Standard HTML Layout
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Page Title</title>
  </head>
  <body>
    <h1>Example Heading</h1>
    <p>Example paragraph.</p>
  </body>
</html>
````

### Structure Breakdown

| Element           | Purpose                           |
| ----------------- | --------------------------------- |
| `<!DOCTYPE html>` | Declares HTML5                    |
| `<html>`          | Root element                      |
| `<head>`          | Metadata (title, scripts, styles) |
| `<body>`          | Visible page content              |
| `<h1>`            | Heading                           |
| `<p>`             | Paragraph                         |

**SOC Insight:**

* Everything in HTML is visible to the user
* Never trust frontend secrecy

---

## 5. HTML Attributes

### Attribute Definition

**Definition:**
Attributes provide **additional information** about an HTML element.

Examples:

```html
<p class="bold-text">Text</p>
<img src="img/cat.jpg">
<p id="example">Unique</p>
```

### Key Attributes

| Attribute | Purpose                   |
| --------- | ------------------------- |
| class     | Styling multiple elements |
| id        | Unique element identifier |
| src       | Resource location         |

**SOC Reality:**

* IDs used by JavaScript → attack surface
* Hardcoded values often leak data

---

## 6. Viewing Page Source (Critical SOC Skill)

### Why It Matters

**Definition:**
Page source shows the **raw HTML, CSS, and JavaScript** sent by the server.

### How to View

* Right-click → **View Page Source**
* Browser DevTools

**SOC Checklist:**

* Hardcoded credentials
* Hidden URLs
* API endpoints
* Comments leaking secrets

---

## 7. JavaScript (JS)

### JavaScript Definition

**Definition:**
JavaScript is a programming language that makes web pages **interactive and dynamic**.

### What JavaScript Does

* Handles user input
* Updates content dynamically
* Controls animations and logic

Example:

```javascript
document.getElementById("demo").innerHTML = "Hack the Planet";
```

---

## 8. JavaScript Events

### Event Definition

**Definition:**
Events trigger JavaScript actions based on user interaction.

Example:

```html
<button onclick='document.getElementById("demo").innerHTML = "Button Clicked";'>
Click Me!
</button>
```

**SOC Insight:**

* Inline JS = poor security practice
* Client-side logic can be abused

---

## 9. Sensitive Data Exposure (Frontend)

### Sensitive Data Exposure Definition

**Definition:**
Sensitive Data Exposure occurs when **confidential information is left accessible** in client-side code.

### Common Examples

* HTML comments with credentials
* API keys in JavaScript
* Hidden admin links
* Test usernames/passwords

Example (Very Bad):

```html
<!-- TODO: remove test credentials admin:password123 -->
```

**SOC Reality:**

* This is a real-world breach cause
* Always inspect page source first

---

## 10. Why Frontend Exposure Is Dangerous

**Impact:**

* Unauthorized access
* Privilege escalation
* Backend compromise

**SOC Rule:**

> If the browser can see it, an attacker can too.

---

## 11. HTML Injection

### HTML Injection Definition

**Definition:**
HTML Injection occurs when **unsanitized user input** is displayed as raw HTML on a web page.

### Why It Happens

* User input is trusted
* No input filtering/sanitization

---

## 12. How HTML Injection Works

### Vulnerable Flow

1. User submits input
2. Input is displayed directly
3. Browser interprets it as HTML

Example attack input:

```html
<h1>You Are Hacked</h1>
```

Result:

* Page content is modified
* Attacker controls appearance

---

## 13. Why HTML Injection Is Dangerous

**Risks:**

* Page defacement
* Credential theft
* Stepping stone to XSS

**SOC Insight:**

* HTML Injection = client-side vulnerability
* Often leads to more severe attacks

---

## 14. Input Sanitization

### Input Sanitization Definition

**Definition:**
Input sanitization is the process of **filtering or encoding user input** to prevent execution.

### Best Practice

* Never trust user input
* Strip or encode HTML tags
* Validate input server-side

**SOC Rule:**

> User input is hostile until proven safe.

---

## 15. Front End vs Back End (Security View)

| Aspect        | Front End        | Back End                 |
| ------------- | ---------------- | ------------------------ |
| Location      | Browser          | Server                   |
| Visibility    | Public           | Hidden                   |
| Trust Level   | None             | High                     |
| Common Issues | Injection, leaks | Auth bypass, logic flaws |

---

## 16. SOC Analyst First Actions (Web App)

When assessing a web application:

1. View page source
2. Check JavaScript files
3. Look for credentials/comments
4. Inspect forms and inputs
5. Identify client-side validation
6. Assume backend is target

---

## 17. Key Takeaways for SOC Analysts

* Websites are client–server systems
* HTML is fully visible to users
* JavaScript can be abused
* Sensitive data exposure is common
* HTML injection is caused by trust failure
* Frontend security mistakes enable backend compromise

---

## 18. Important Acronyms (SOC Must-Know)

| Acronym | Meaning                           |
| ------- | --------------------------------- |
| HTML    | HyperText Markup Language         |
| CSS     | Cascading Style Sheets            |
| JS      | JavaScript                        |
| GUI     | Graphical User Interface          |
| HTTP    | HyperText Transfer Protocol       |
| HTTPS   | HTTP Secure                       |
| XSS     | Cross-Site Scripting              |
| API     | Application Programming Interface |

---
