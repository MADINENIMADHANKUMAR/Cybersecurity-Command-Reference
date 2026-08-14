# Scanning & Enumeration

### Quick full port scan

```
nmap -p- --min-rate=1000 -T4 <target-ip> -oN full-ports.txt
```

**Use when:** First pass on a new target — find every open port fast before going deeper.

---

### Detailed scan on discovered ports

```
nmap -p<ports> -sC -sV -oN detailed.txt <target-ip>
```

**Use when:** Following up the fast scan — grabs service versions and runs default NSE scripts.

---

### UDP top ports scan

```
nmap -sU --top-ports 100 <target-ip>
```

**Use when:** TCP looks locked down or you suspect SNMP/DNS/NTP services.

**Note:** UDP scans are slow — narrow the port list.

---

### Aggressive scan with OS detection

```
nmap -A <target-ip>
```

**Use when:** You want OS fingerprint, traceroute, and script scan all in one (noisy, not stealthy).

---

### Vulnerability scan with NSE scripts

```
nmap --script vuln <target-ip>
```

**Use when:** Checking discovered services against nmap's known-vulnerability script set.

---

### Scan a whole subnet for live hosts

```
nmap -sn <subnet>/24
```

**Use when:** Discovering live hosts before scanning individual boxes.

---

### Enumerate SMB shares

```
smbclient -L //<target-ip>/ -N
smbmap -H <target-ip>
```

**Use when:** Checking for null-session SMB access and listing available shares.

---

### Enumerate SMB users/groups

```
enum4linux -a <target-ip>
```

**Use when:** Pulling users, groups, shares, and password policy from a Windows/Samba host.

---

### Enumerate NFS exports

```
showmount -e <target-ip>
```

**Use when:** Checking for exposed NFS shares that might be mountable without auth.

---

### Web server enumeration with whatweb

```
whatweb <target-ip>
```

**Use when:** Quickly fingerprinting the tech stack (CMS, server, frameworks) behind a web port.

---

### Enumerate SNMP

```
snmpwalk -c public -v1 <target-ip>
```

**Use when:** SNMP (UDP 161) is open — default community strings often leak a lot of host info.
