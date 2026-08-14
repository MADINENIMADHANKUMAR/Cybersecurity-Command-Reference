# Setting Up Your Hacking Lab & Tools

### Update and prep Kali/Parrot

```
sudo apt update && sudo apt full-upgrade -y
```

**Use when:** First thing after spinning up a new attack VM.

---

### Install SecLists wordlists

```
sudo apt install seclists -y
```

**Use when:** You need broader wordlist coverage than the default rockyou.txt.

---

### Connect to a VPN lab (HTB/THM-style OpenVPN)

```
sudo openvpn <lab-name>.ovpn
```

**Use when:** Joining a CTF platform's lab network before starting a box.

---

### Add a target to /etc/hosts

```
echo "<target-ip> <target-hostname>" | sudo tee -a /etc/hosts
```

**Use when:** A box relies on virtual hosting and you need the hostname to resolve locally.

---

### Set up a Python virtual environment for a tool

```
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

**Use when:** Installing a Python-based offensive tool without polluting your system packages.

---

### Install Go-based recon tools

```
go install github.com/OJ/gobuster/v3@latest
go install github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
go install github.com/projectdiscovery/httpx/cmd/httpx@latest
```

**Use when:** Bootstrapping a fresh recon toolkit — make sure `$GOPATH/bin` is on your `PATH`.

---

### Spin up a vulnerable target with Docker

```
docker run -d -p 80:80 vulnerables/web-dvwa
```

**Use when:** Practicing web app attacks locally without needing a hosted CTF box.

---

### Snapshot a VM before testing

```
VBoxManage snapshot "<vm-name>" take "clean-state"
```

**Use when:** Before running anything destructive/exploit-heavy in a local VirtualBox lab — easy rollback.
