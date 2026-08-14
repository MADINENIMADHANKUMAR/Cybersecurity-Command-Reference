# Introduction to CTF Creation & Environment Setup

Placeholder — fill in as you go through this part of the course. Suggested starting points below.

### Spin up a vulnerable VM for a custom box

```
VBoxManage createvm --name "<box-name>" --ostype "Ubuntu_64" --register
```

**Use when:** Starting a new custom CTF box build from scratch.

---

### Host a custom box on a local network for testing

```
python3 -m http.server 80
```

**Use when:** Quick sanity-check that your intentionally-vulnerable service is reachable before packaging it.

---

### Package a VM for distribution (OVA)

```
VBoxManage export "<vm-name>" -o box-release.ova
```

**Use when:** Finalizing a custom CTF box for sharing/submission.

---

## To fill in as the course covers it:
- [ ] Designing a vulnerability chain (initial access -> privesc) intentionally
- [ ] Writing challenge descriptions / hints
- [ ] Setting flag placement conventions (user.txt / root.txt locations)
- [ ] Testing methodology — walking your own box as an attacker before release
- [ ] Marketplace submission requirements (per platform: HTB, THM, etc.)
