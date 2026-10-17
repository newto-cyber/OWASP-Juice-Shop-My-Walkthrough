# OWASP Juice Shop Walkthrough

Personal walkthrough notes, methodology breakdowns, and solutions for challenges in OWASP Juice Shop.

> [!WARNING]
> **Spoiler and Learning Advisory**
> If you are currently working through OWASP Juice Shop challenges or planning to use it to learn web application security, reviewing these writeups beforehand is strongly discouraged. Solving the challenges independently provides far greater learning value. Refer to these notes only after attempting the challenges or when comparing alternative exploitation techniques.

## Repository Structure

The repository is organized by vulnerability classification:

- **Broken-Access-Control**: Privilege escalation, horizontal/vertical authorization bypass, and insecure direct object references (IDOR).
- **Broken-Anti-Automation**: Rate limiting bypasses, CAPTCHA avoidance, and automated abuse.
- **Broken-Authentication**: Weak credential handling, session management flaws, and authentication bypasses.
- **Cross-Site-Scripting**: Reflected, stored, and DOM-based XSS attacks.
- **Cryptographic-Issues**: Weak cryptography algorithms, insecure keys, and flawed token generation.
- **Improper-Input-Validation**: Input sanitization bypasses and client-side validation circumvention.
- **Injection**: SQL injection, command injection, and related injection flaws.
- **Insecure-Deserialization**: Exploiting untrusted data deserialization.
- **Miscellaneous**: General application challenges and edge-case exploits.
- **Observability-Failures**: Issues related to insufficient logging, monitoring, and error exposure.
- **Security-Misconfiguration**: Unnecessary features enabled, default configurations, and improper headers.
- **Security-through-Obscurity**: Hidden endpoints, disguised assets, and secrets hidden in comments or paths.
- **Sensitive-Data-Exposure**: Unprotected confidential data, leaked API keys, and sensitive backups.
- **Tutorials**: Preliminary onboarding tasks.
- **Unvalidated-Redirects**: Open redirect flaws and untrusted forwarding.
- **Vulnerable-Components**: Known vulnerabilities in third-party libraries and dependencies.
- **XML-External-Entities**: XML parsing attacks and external entity injection (XXE).

## Documentation Structure

Walkthrough entries follow a consistent structure:
- Objective and section overview
- Official references
- Considered approaches
- Step-by-step solution methodology

## References

- [OWASP Juice Shop Official Project](https://owasp.org/www-project-juice-shop/)
- [Pwning OWASP Juice Shop Companion Guide](https://pwning.owasp-juice.shop/)
