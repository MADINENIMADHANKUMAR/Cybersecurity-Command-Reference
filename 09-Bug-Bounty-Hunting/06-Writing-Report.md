# Writing a Bug Bounty / Pentest Report

Not a command list — a structure to keep every finding consistent and easy for a triager to act on.

### Standard finding template

```markdown
## [Severity] Title of the Vulnerability

**Summary:** One or two sentences — what it is and why it matters.

**Steps to Reproduce:**
1. ...
2. ...
3. ...

**Proof of Concept:**
(screenshot, request/response, or PoC script)

**Impact:**
What an attacker could actually do with this (data exposure, account takeover, RCE, etc.)

**Remediation:**
Concrete fix — not just "sanitize input," name the specific control.

**References:**
CWE / OWASP category / relevant CVE if applicable
```

**Use when:** Writing up any confirmed finding for a client report or bug bounty submission.

**Note:** Triagers reward *reproducibility* — a vague report with no clear steps gets bounced regardless of severity. Always attach a request/response pair or a script, not just a description.

---

### Severity quick-reference (CVSS-style bucket)

```
Critical  — Full system compromise / mass data breach, low complexity
High      — Significant data exposure or account takeover, some complexity
Medium    — Limited impact or requires specific conditions/user interaction
Low       — Minimal impact, mostly informational or defense-in-depth
```

**Use when:** Assigning a severity label before submission — most triage systems expect this to already be reasoned through.
