# Cybersecurity Command Reference

A personal quick-reference of commands, tools, and techniques for penetration testing, bug bounty hunting, and CTF work — organized to follow a standard ethical hacking course curriculum, from fundamentals through initial access, privilege escalation, and CTF creation.

## ⚠️ Legal & Ethical Use

Everything in this repo is for **authorized testing only** — your own lab, a CTF platform (HTB, THM, etc.), or an engagement you have **explicit written permission** for. Running any of this against systems you don't own or aren't authorized to test is illegal in most jurisdictions. This repo is study material, not a green light.

## Structure

| Folder | Covers |
|---|---|
| `01-Fundamentals-OS-Networking` | Linux/Windows networking basics, routing, file transfer |
| `02-Information-Gathering` | OSINT, WHOIS, DNS, subdomain enum, Google dorking |
| `03-Scanning-Enumeration` | Nmap, SMB/NFS/SNMP enum, service fingerprinting |
| `04-Vulnerabilities-Exploitation` | Metasploit, msfvenom, searchsploit, SQLi |
| `05-Specialized-Techniques` | MITM, ARP/DNS spoofing, Responder, Kerberoasting, pass-the-hash |
| `06-DoS-Steg-WiFi` | DoS testing, steganography extraction, WPA/WPA2 cracking |
| `07-Crypto-Password-Cracking` | Cipher identification, John, Hashcat, wordlist generation |
| `08-Social-Engineering-Sniffing` | SET, phishing simulation, tcpdump/Wireshark sniffing |
| `09-Bug-Bounty-Hunting` | Recon, injection, access control, web app & advanced vulns, report writing |
| `10-Lab-Setup-Tools` | Lab environment setup, tool installation |
| `11-CTF` | Methodology, initial access, Linux/Windows privesc, reverse proxies, box creation |
| `templates` | Entry format template for adding new commands consistently |

## Entry Format

Every command entry follows the same shape so the reference stays scannable:

```markdown
### <Short Title>

​```
<command>
​```

**Use when:** <the situation that calls for this>

**Note:** <optional — gotchas, flags, follow-up step>
```

See `templates/command-template.md` to copy directly when adding new entries.

## How I'm using this

- Course notes get filed into the matching numbered folder as I go through each module.
- CTF box walkthroughs and write-ups get their own entries under `11-CTF` once solved (don't paste full write-ups from other authors — capture your own commands/approach).
- `09-Bug-Bounty-Hunting` doubles as my live bug bounty methodology — updated whenever I find a technique that actually lands a bounty.
