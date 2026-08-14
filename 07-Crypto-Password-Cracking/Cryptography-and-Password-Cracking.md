# Cryptography & Password Cracking

## Cryptography (CTF-style)

### Identify a hash type

```
hashid <hash>
hash-identifier
```

**Use when:** You have a hash and don't know its algorithm yet.

---

### Base64 decode

```
echo "<string>" | base64 -d
```

**Use when:** Anything that looks like base64 padding (`==` or `=` at the end) turns up.

---

### ROT13 / Caesar cipher decode

```
echo "<string>" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

**Use when:** Text looks like scrambled English — classic CTF crypto starter.

---

### Identify/crack classical ciphers automatically

```
python3 -m ciphey -t "<ciphertext>"
```

**Use when:** Unknown encoding/cipher chain — Ciphey will try to auto-detect and decode.

---

## Password Cracking

### Crack a hash with John the Ripper

```
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
john --show hash.txt
```

**Use when:** You have a hash file and a wordlist and want offline cracking.

---

### Extract a hash for John (zip/rar/pdf/ssh key)

```
zip2john file.zip > hash.txt
rar2john file.rar > hash.txt
pdf2john.py file.pdf > hash.txt
ssh2john id_rsa > hash.txt
```

**Use when:** The protected file itself isn't directly crackable — convert to a John-compatible hash first.

---

### Crack a hash with Hashcat

```
hashcat -m <mode> -a 0 hash.txt /usr/share/wordlists/rockyou.txt
```

**Use when:** GPU-accelerated cracking is available — much faster than John for large hash sets.

**Note:** `-m` mode must match the hash type (e.g. 0 = MD5, 1000 = NTLM, 1800 = sha512crypt).

---

### Hashcat with rules (mangled wordlist attack)

```
hashcat -m <mode> -a 0 hash.txt rockyou.txt -r /usr/share/hashcat/rules/best64.rule
```

**Use when:** Straight wordlist attack fails — rule-based mangling covers common password variations.

---

### Generate a custom wordlist with CeWL

```
cewl <target-url> -m 5 -w custom-wordlist.txt
```

**Use when:** Building a target-specific wordlist from words scraped off their own website.

---

### Crack a hash online lookup (rainbow table check)

```
curl -s "https://hashtoolkit.com/reverse-hash?hash=<hash>"
```

**Use when:** Quick check for common/already-cracked hashes before spinning up local cracking.

**Note:** Only use for CTF/lab hashes — never submit real credential hashes to a third-party service.
