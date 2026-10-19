# Cybersecurity Portfolio — Vulnversity Penetration Test

**ITECH1502 Cybersecurity Fundamentals — Final Project**
Ish Chander · Federation University

## Overview
A hands-on web application penetration test of the **Vulnversity**  machine on
**TryHackMe** that I completed for my final project **ITECH1502**. It shows a full
attack chain. From reconnaissance to full administrator (root) access and controls to prevent each weakness.
## Platform & Tools
- **Platform:** TryHackMe (browser-based labs with live VMs)
- **Nmap** — network scanning and service enumeration
- **Gobuster** — directory brute forcing
- **Burp Suite** — upload-filter testing (Intruder)
- **Netcat** — reverse-shell listener
- **Linux** — privilege escalation via SUID

## The Attack Chain
1. **Reconnaissance** — Nmap found 6 open ports and an Apache web server on port 3333.
2. **Enumeration** — Gobuster found a hidden `/internal` upload page.
3. **Exploitation** — bypassed the upload filter with a `.phtml` extension and
   uploaded a PHP reverse shell, gaining a foothold as `www-data`.
4. **Privilege Escalation** — abused a misconfigured SUID bit on `/bin/systemctl`
   to gain root.

## Key Findings
| Weakness | Impact |
| --- | --- |
| Web server on non-standard port 3333 | Larger attack surface |
| Hidden `/internal` upload page | Reachable without authentication |
| Weak file-type block-list (`.phtml` allowed) | Remote code execution |
| SUID on `/bin/systemctl` | Full root compromise |


## Lessons Learned
Small individual weaknesses plus a weak upload filter and one misconfigured SUID binary can be chained into a full system compromise. This project made the principles of **defence in depth** and **least privilege** stick with me and reflects the daily work of an SOC analyst and penetration tester.

## Screenshots
Evidence of each stage is in the [`/screenshots`](./screenshots) folder.


## Links
-  **Project Report** — [Download the report](./ITECH1502%20Final%20Project%20Report%20%E2%80%93%20Vulnversity%20%28TryHackMe%29.docx)
-  **Video Presentation** — [Watch on YouTube](https://youtu.be/zZc-AgxrDPI?si=SVv5EAWuQy_IUcwa)
-  **Screenshots / Evidence** — see the [`/screenshots`](./screenshots) folder

---
*Completed for ITECH1502, Federation University, 2026.*
