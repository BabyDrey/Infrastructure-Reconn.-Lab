# Infrastructure-Reconn.-Lab
A hands-on laboratory report covering active and passive footprinting methodologies using tools like dnsenum, wafw00f, whatweb, theHarvester, and Sublist3r.
# Lab Report: Infrastructure Reconnaissance and Target Footprinting

## 📌 Executive Summary
This laboratory exercise focused on information gathering methodologies, mapping target attack surfaces across public infrastructure. The objective was to practice both passive and active reconnaissance techniques using industry-standard tools within Kali Linux (`dnsenum`, `wafw00f`, `whatweb`, `theHarvester`, and `Sublist3r`). The data gathered provides insight into DNS topology, firewall protections, application stacks, and leaked organizational metadata.

---

## 🔍 Core Concepts: Active vs. Passive Reconnaissance

Information gathering is split into two primary methodologies:
* **Passive Reconnaissance:** Gathering data without interacting directly with the target infrastructure. This relies on publicly available third-party registries, archives, and search records. 
  * *Examples:* Reviewing WHOIS lookup data, scraping social media profiles, or searching Google hacking databases (GHDB).
* **Active Reconnaissance:** Engaging the target system directly by sending network packets to probe for open doors, responses, and configurations.
  * *Examples:* Running port scans, banner grabbing from active ports, or probing application endpoints.

---

## 🛠️ Hands-On Lab Work & Tool Execution

### 1. DNS Reconnaissance
DNS reconnaissance maps out an organization's public servers, mail routing nodes, and subdomains to pinpoint network boundaries.
* **Tool Used:** `dnsenum`
* **Target Domain:** `zero.webappsecurity.com`
* **Objective:** Enumerate DNS resource records (A, TXT, MX) and perform basic subdomain scraping.
* **Execution:** Spun up `dnsenum` against the target to pull authoritative nameservers and map network location parameters.
* <img width="672" height="538" alt="dnsenum of test website" src="https://github.com/user-attachments/assets/e2373c43-fb5d-4439-9bb0-7f0405c51977" />

---

### 2. Firewall Reconnaissance
Firewall reconnaissance checks for Web Application Firewalls (WAF) or intrusion prevention layers before running loud network scans.
* **Tool Used:** `wafw00f`
* **Target Domain:** `hiit.ng`
* **Objective:** Fingerprint backend security proxies by analyzing distinct HTTP response headers and cookies.
* **Execution:** Ran the active analyzer against the host to detect if traffic was being intercepted by commercial security filters.
<img width="1365" height="717" alt="wafw00f test on hiit ng" src="https://github.com/user-attachments/assets/5e1b8464-3670-49cd-bb44-2e1efd364b6d" />

---

### 3. Web Technology Reconnaissance
Web reconnaissance identifies application frameworks, content management systems (CMS), server engines, and tracking scripts.
* **Tool Used:** `whatweb`
* **Target Domain:** `zero.webappsecurity.com`
* **Objective:** Extract server header signatures and backend framework versions without a disruptive vulnerability scan.
* **Execution:** Utilized the tool to identify server configurations, backend software versions, and embedded libraries.
<img width="704" height="562" alt="Use of whatweb to scan test website" src="https://github.com/user-attachments/assets/fddaaa4a-5e90-4401-9296-7b3896176745" />

---

### 4. Email & Metadata Reconnaissance
Email footprinting builds an initial target list for social engineering assessments or identifying exposed corporate user accounts.
* **Tool Used:** `theHarvester`
* **Objective:** Mine public search engine caches and PGP key servers to extract corporate email schemas, employee names, and subdomains.
* **Execution:** Configured the tool to run passive OSINT queries across open search engines to pull data tied to the organizational domain.
<img width="751" height="556" alt="Use of theHarvester on test domanin 2" src="https://github.com/user-attachments/assets/c2ca5dd7-bf22-4485-b38b-e11e85cb17b9" />

---

### 5. Subdomain Enumeration (Troubleshooting Session)
Subdomain scraping expands the target scope to find unmonitored development servers or legacy interfaces.
* **Tool Used:** `Sublist3r`
* **Lab Status:** **Encountered Execution Errors**
* **Technical Analysis:** While attempting brute-force and OSINT scraping with `Sublist3r`, the script threw execution errors. 
* **Troubleshooting Note:** Many modern search engine APIs (like Google, Bing, and Baidu) have updated their bot-detection rate limits and CAPTCHAs since Sublist3r's last public repository update. This causes python scraping libraries to throw errors when they try to parse unauthenticated web data.
<img width="698" height="541" alt="Error encountered while practicing with sublist3r" src="https://github.com/user-attachments/assets/6605f1c1-7c39-47b6-9084-a62e11bd0779" />

---

## 🧹 Clean-Up & Reset
Since all activities in this lab involved command-line profiling and basic terminal tools, no background payloads or local services were left running. The environment is clean and safe.
