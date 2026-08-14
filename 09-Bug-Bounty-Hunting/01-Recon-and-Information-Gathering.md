# Bug Bounty — Recon & Information Gathering

### Full subdomain sweep + live host check

```
subfinder -d <domain> -silent | httpx -silent -o live-hosts.txt
```

**Use when:** Standard bug bounty recon opener — find subdomains, then confirm which ones actually serve HTTP(S).

---

### Directory/file brute force on a live target

```
gobuster dir -u https://<target> -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-medium-directories.txt -x php,html,txt -o gobuster-out.txt
```

**Use when:** Enumerating hidden endpoints/files on a confirmed live web app.

---

### Parameter discovery

```
arjun -u https://<target>/endpoint
```

**Use when:** Finding hidden/undocumented GET or POST parameters an app might accept.

---

### Crawl a site for endpoints

```
katana -u https://<target> -o endpoints.txt
```

**Use when:** Mapping out the full attack surface (JS-rendered links included) of a target app.

---

### Extract endpoints from JS files

```
cat endpoints.txt | grep '\.js$' | while read url; do curl -s "$url" | grep -Eo "(\"|')(\/[a-zA-Z0-9_?&=\/\-\#\.]*)(\"|')" ; done
```

**Use when:** Hunting for API routes or secrets accidentally exposed in client-side JavaScript.

---

### Check for subdomain takeover

```
subzy run --targets subdomains.txt
```

**Use when:** A subdomain CNAMEs to a service (S3, GitHub Pages, Heroku, etc.) that's no longer claimed.
