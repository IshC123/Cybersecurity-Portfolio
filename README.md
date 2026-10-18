# Cybersecurity-Portfolio
# Cybersecurity Portfolio — Vulnversity Penetration Test

**ITECH1502 Cybersecurity Fundamentals — Final Project**
ISH CHANDER

## Overview
A hands-on web application penetration test of the **Vulnversity** machine on
**TryHackMe**, completed as my ITECH1502 final project. It demonstrates a full
attack chain — from reconnaissance to full administrator (root) access — and
the controls that prevent each weakness.

## Platform & Tools
- **Platform:** TryHackMe (browser-based labs with live VMs)
- **Nmap** — network scanning and service enumeration
- **Gobuster** — directory brute-forcing
- **Burp Suite** — upload-filter fuzzing (Intruder)
- **Netcat** — reverse-shell listener
- **Linux** — privilege escalation via SUID

## The Attack Chain
1. **Reconnaissance** — Nmap found 6 open ports and an Apache web server on port 3333.
2. **Enumeration** — Gobuster uncovered a hidden `/internal` upload page.
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

## Screenshots
 

## Lessons Learned
Small, individually minor weaknesses chain together into full compromise.
Strong defences — validating uploads by content, least privilege, and auditing
SUID binaries — break that chain. I also strengthened my troubleshooting skills
working through proxy setup, session timeouts and shell timing.

## Links

*Completed for ITECH1502, Federation University.*
