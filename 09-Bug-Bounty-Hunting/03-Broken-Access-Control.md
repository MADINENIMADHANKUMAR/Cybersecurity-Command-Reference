# Bug Bounty — Broken Access Control

### IDOR test — swap an object ID

```
GET /api/user/1001/profile   ->   GET /api/user/1002/profile
```

**Use when:** An endpoint takes a user/object ID — check whether you can access another user's data by changing it.

---

### Force browsing to admin/restricted paths

```
gobuster dir -u https://<target> -w /usr/share/wordlists/seclists/Discovery/Web-Content/CMS/admin-panels.txt
```

**Use when:** Checking for admin panels or restricted paths not linked from the normal UI.

---

### Test for privilege escalation via role parameter tampering

```
{"role": "user"}   ->   {"role": "admin"}
```

**Use when:** A request body/JSON includes a role or permission field — try elevating it client-side.

---

### Test HTTP method override for auth bypass

```
curl -X POST https://<target>/admin/delete -H "X-HTTP-Method-Override: GET"
```

**Use when:** A protected endpoint blocks one HTTP verb but might trust an override header for another.

---

### Test for missing function-level access control

```
curl -s https://<target>/api/admin/users -H "Authorization: Bearer <low-priv-token>"
```

**Use when:** Checking whether an admin-only API endpoint actually validates the caller's privilege level.

---

### JWT tampering — decode and inspect

```
echo "<jwt-part>" | base64 -d
```

**Use when:** Inspecting a JWT's header/payload for algorithm confusion or role claims you might tamper with.

---

### JWT "alg: none" bypass test

```
python3 -c "import jwt; print(jwt.encode({'user':'admin'}, key='', algorithm='none'))"
```

**Use when:** Testing whether the backend still accepts unsigned tokens.
