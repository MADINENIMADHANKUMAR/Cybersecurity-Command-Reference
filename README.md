# Cybersecurity Command Reference

A personal quick-reference of commands, techniques, and workflows for cybersecurity, penetration testing, bug bounty hunting, and CTFs. Organized by topic for fast reference during learning and authorized security testing.

## ⚠️ Legal & Ethical Use

This repository is intended for **authorized security testing and educational purposes only** — including personal labs, CTF platforms such as HTB and THM, and engagements where you have explicit permission.

Do not use these techniques against systems you do not own or have authorization to test.

## Structure

| Folder | Covers |
|---|---|
| `01-Fundamentals-OS-Networking` | Linux/Windows networking basics, routing, and file transfer |
| `02-Information-Gathering` | OSINT, WHOIS, DNS, subdomain enumeration, and Google dorking |
| `03-Scanning-Enumeration` | Nmap, SMB/NFS/SNMP enumeration, and service fingerprinting |
| `04-Vulnerabilities-Exploitation` | Metasploit, msfvenom, SearchSploit, and SQL injection |
| `05-Specialized-Techniques` | MITM, ARP/DNS spoofing, Responder, Kerberoasting, and pass-the-hash |
| `06-DoS-Steg-WiFi` | DoS testing, steganography, and WiFi security testing |
| `07-Crypto-Password-Cracking` | Cryptography, John the Ripper, Hashcat, and password cracking |
| `08-Social-Engineering-Sniffing` | Social engineering, phishing simulations, tcpdump, and Wireshark |
| `09-Bug-Bounty-Hunting` | Recon, injection, access control, web vulnerabilities, and reporting |
| `10-CTF` | CTF methodology, initial access, privilege escalation, pivoting, and box creation |
| `templates` | Templates for adding new command entries |

## Entry Format

Every command entry follows a consistent format:

```markdown
### <Short Title>

<command>

**Use when:** <the situation that calls for this>

**Note:** <optional — gotchas, flags, or follow-up steps>
