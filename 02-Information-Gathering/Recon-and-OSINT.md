# Information Gathering / OSINT

### WHOIS lookup

```
whois <domain>
```

**Use when:** Starting recon on a domain — registrar, name servers, registration dates.

---

### DNS record enumeration

```
dig ANY <domain>
dig A <domain>
dig MX <domain>
dig TXT <domain>
```

**Use when:** Mapping a target's DNS footprint (mail servers, TXT/SPF records, subdomains hinted at in records).

---

### Reverse DNS lookup

```
dig -x <ip>
```

**Use when:** Identifying what hostname resolves to a discovered IP.

---

### Subdomain enumeration (passive)

```
subfinder -d <domain> -o subdomains.txt
```

**Use when:** Building an initial subdomain list without touching the target directly.

---

### Subdomain enumeration (brute force)

```
gobuster dns -d <domain> -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt
```

**Use when:** Passive tools come up short and you want to actively brute-force subdomains.

---

### Amass full recon

```
amass enum -d <domain> -o amass-results.txt
```

**Use when:** Doing a deeper, slower subdomain/asset enumeration pass than subfinder.

---

### theHarvester for emails/hosts

```
theHarvester -d <domain> -b all -f harvester-results
```

**Use when:** Collecting emails, hostnames, and employee names from public sources for a social engineering or password spray plan.

---

### Google dorking (manual)

```
site:<domain> filetype:pdf
site:<domain> intitle:"index of"
site:<domain> inurl:admin
```

**Use when:** Looking for exposed documents, open directories, or login panels indexed by search engines.

---

### Wayback machine URLs

```
waybackurls <domain> > wayback.txt
```

**Use when:** Pulling historical URLs that might reveal old, forgotten, or unlinked endpoints.

**Note:** Requires the `waybackurls` Go tool (`go install github.com/tomnomnom/waybackurls@latest`).

---

### Shodan search (CLI)

```
shodan search "hostname:<domain>"
```

**Use when:** Checking what's already indexed publicly about the target's exposed services.

**Note:** Requires `shodan init <api-key>` first.
