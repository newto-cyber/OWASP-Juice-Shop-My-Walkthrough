# [WSTG-XXXX-XX] Finding Title

| Metadata | Details |
| :--- | :--- |
| **WSTG ID** | `WSTG-XXXX-XX` |
| **WSTG Category** | Category Name (e.g., Information Gathering) |
| **Target Endpoint** | `http://localhost:3000/...` |
| **CWE / OWASP Top 10** | `CWE-XXX` / `A0X:2021` |
| **Severity** | Informational / Low / Medium / High / Critical |
| **Juice Shop Challenge** | Challenge Name |

---

## Summary

Provide a concise overview of the vulnerability or security mechanism under test, explaining why the flaw occurs in the target application and its security implications.

---

## Test Objectives

- Identify the specific application behavior, endpoint, or control to evaluate.
- Determine whether the implementation exposes sensitive data or allows unauthorized actions.

---

## How to Test

### Black-Box Testing

Document step-by-step reconnaissance, input probing, and exploitation from an external tester's perspective without prior access to backend source code.

#### Request / Action
```http
GET /target-endpoint HTTP/1.1
Host: localhost:3000
```

#### Observed Response / Evidence
Document the HTTP response, DOM state, or application behavior proving the finding.

### Gray-Box / Source Code Review

Document client-side bundle inspection (`main.js`), API schema analysis, or configuration review that confirms how the vulnerability functions under the hood.

---

## Remediation

- **Primary Control:** Specify the architectural or code-level fix required to address the root cause.
- **Secondary Hardening:** Outline defense-in-depth measures to mitigate residual risk.

---

## Tools

- Browser Developer Tools (Network / Sources / Storage)
- Intercepting Proxy (OWASP ZAP / Burp Suite)
- Additional CLI tools used (e.g., `curl`, `ffuf`, `sqlmap`)

---

## References

- [OWASP Web Security Testing Guide - WSTG-XXXX-XX](https://owasp.org/www-project-web-security-testing-guide/)
- [OWASP Juice Shop Companion Guide](https://pwning.owasp-juice.shop/)
