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
1. **Reconnaissance** — I started with an Nmap scan, which turned up 6 open ports
   and an Apache web server sitting on port 3333.
2. **Enumeration** — Running Gobuster against that server uncovered a hidden
   `/internal` page where files could be uploaded.
3. **Exploitation** — The upload page tried to block dangerous files, but its filter
   was weak. I slipped a `.phtml` file past it, uploaded a PHP reverse shell, and
   landed a foothold on the server as the `www-data` user.
4. **Privilege Escalation** — From there I found that `/bin/systemctl` had a
   misconfigured SUID bit, and abused it to escalate all the way to root.

   
## Key Findings
| Weakness | What it allowed |
| --- | --- |
| Web server on an unusual port (3333) | A wider attack surface once discovered |
| Hidden `/internal` upload page | Access without any authentication |
| Weak file-type filter (`.phtml` slipped through) | Remote code execution on the server |
| SUID set on `/bin/systemctl` | The final step to full root access |


## Lessons Learned
Small individual weaknesses plus a weak upload filter and one misconfigured SUID binary can be chained into a full system compromise. This project made the principles of **defence in depth** and **least privilege** stick with me and reflects the daily work of an SOC analyst and penetration tester.

## Screenshots
Evidence of each stage is in the [`/screenshots`](./screenshots) folder.


## Links
-  **Project Report** — [Download the report](https://github.com/IshC123/Cybersecurity-Portfolio/blob/main/ITECH1502-Vulnversity-Report.docx)
-  **Video Presentation** — [Watch on YouTube](https://youtu.be/zZc-AgxrDPI?si=SVv5EAWuQy_IUcwa)
-  **Screenshots / Evidence** — see the [`/screenshots`](./screenshots) folder

---
*Completed for ITECH1502, Federation University, 2026.*
