# Operating Systems & Networking

### Check IP configuration (Linux)

```
ip a
```

**Use when:** Confirming your own interface/IP before starting any engagement (lab, VPN, or CTF box).

---

### Check IP configuration (Windows)

```
ipconfig /all
```

**Use when:** Working from a Windows attack box or checking a compromised Windows host's network config.

---

### Add a route through a gateway

```
sudo ip route add <target-subnet>/24 via <gateway-ip>
```

**Use when:** You need traffic to an internal subnet routed through a pivot/gateway.

---

### Check routing table

```
ip route
```

**Use when:** Confirming which interface/gateway traffic to a target will use.

---

### Basic connectivity test

```
ping -c 4 <target-ip>
```

**Use when:** Confirming a host is up before scanning.

**Note:** ICMP is often blocked — a dead ping doesn't mean a dead host, just move to a port scan.

---

### Trace the path to a host

```
traceroute <target-ip>
```

**Use when:** Mapping network topology, or figuring out why a target is unreachable.

---

### Check open TCP connections/listening ports (Linux)

```
ss -tulnp
```

**Use when:** Enumerating what's listening locally on a box you've landed on.

---

### Check open TCP connections/listening ports (Windows)

```
netstat -ano
```

**Use when:** Same as above but on Windows — pair the PID with `tasklist` to identify the process.

---

### Start a simple Python HTTP server

```
python3 -m http.server 8000
```

**Use when:** Serving tools/payloads to a target for download over HTTP.

---

### Transfer a file with SCP

```
scp <file> user@<target-ip>:/path/to/destination
```

**Use when:** Moving files to/from a box you have SSH creds for.
