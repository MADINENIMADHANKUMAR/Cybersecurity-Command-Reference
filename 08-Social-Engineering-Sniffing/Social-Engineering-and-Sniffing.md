# Social Engineering & Sniffing

## Social Engineering

### Launch the Social Engineer Toolkit

```
setoolkit
```

**Use when:** Building an authorized phishing/credential-harvesting scenario for a client engagement.

**Note:** Only within a written, authorized social engineering engagement — never against real users without consent.

---

### Clone a login page for a credential harvester (via SET)

```
1) Social-Engineering Attacks
2) Website Attack Vectors
3) Credential Harvester Attack Method
2) Site Cloner
```

**Use when:** Simulating a phishing landing page as part of an authorized assessment.

---

### Send a test phishing email (authorized engagements only)

```
swaks --to <target-email> --from <spoofed-sender> --server <smtp-server> --header "Subject: <subject>" --body "<body>"
```

**Use when:** Testing an organization's phishing/email defenses under a signed scope.

---

## Sniffing

### Capture traffic with tcpdump

```
sudo tcpdump -i <interface> -w capture.pcap
```

**Use when:** Recording raw traffic on an interface for later analysis in Wireshark.

---

### Filter tcpdump for a specific host/port

```
sudo tcpdump -i <interface> host <target-ip> and port <port>
```

**Use when:** Narrowing a live capture to just the traffic you care about.

---

### Capture HTTP Basic Auth / plaintext creds

```
sudo tcpdump -i <interface> -A | grep -i "pass"
```

**Use when:** Sniffing unencrypted traffic on a shared network segment (lab use) to demonstrate plaintext-auth risk.

---

### Live packet capture with Wireshark from CLI (tshark)

```
tshark -i <interface> -Y "http.request"
```

**Use when:** You want Wireshark-style filtering without the GUI, e.g. over SSH on a headless box.
