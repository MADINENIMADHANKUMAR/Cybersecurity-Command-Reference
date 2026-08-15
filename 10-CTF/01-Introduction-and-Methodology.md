# Introduction to CTF & Methodology

A repeatable approach — not a specific tool — for working through a CTF box start to finish.

### Standard box workflow

```
1. nmap -p- --min-rate=1000 -T4 <ip> -oN full-ports.txt
2. nmap -p<found-ports> -sC -sV -oN detailed.txt <ip>
3. Enumerate every open service (web, SMB, FTP, etc.)
4. Identify a foothold vector (exploit, weak creds, misconfig)
5. Get initial shell -> stabilize TTY
6. Local enumeration (linpeas/winpeas)
7. Privilege escalation
8. Grab flags (user.txt / root.txt or proof.txt / local.txt)
```

**Use when:** Starting literally any CTF machine — this is the loop, every time.

---

### Services-to-checklist quick map

```
21   FTP        -> anonymous login, version exploits
22   SSH        -> creds, key reuse, version exploits
80/443 HTTP(S)  -> gobuster, tech fingerprint, source review
139/445 SMB     -> enum4linux, smbclient, smbmap
3306 MySQL      -> default creds, version exploits
```

**Use when:** Triaging which rabbit hole to go down first after the initial port scan.

---

### Track findings as you go

```
mkdir -p ~/ctf/<box-name>/{scans,loot,exploits,notes}
```

**Use when:** Before you start — keeping scans/loot/notes organized saves real time on longer boxes.
