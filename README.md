# OWASP Juice Shop Penetration Testing Walkthrough (WSTG)

Security testing findings and walkthroughs for OWASP Juice Shop, structured according to the **OWASP Web Security Testing Guide (WSTG)**.

> [!WARNING]
> **Spoiler and Learning Advisory**
> If you are actively working through OWASP Juice Shop challenges to learn web application security, avoid reviewing these writeups beforehand. Solve the challenges independently first, then use these documents to compare testing methodologies and remediation strategies.

## Repository Structure

The repository is organized according to the 12 testing categories of the OWASP Web Security Testing Guide:

- **[Information-Gathering](Information-Gathering/)** (`WSTG-INFO`): Application fingerprinting, client-side bundle analysis, route enumeration, and metadata leakage.
- **[Configuration-and-Deployment-Management-Testing](Configuration-and-Deployment-Management-Testing/)** (`WSTG-CONF`): Server configuration flaws, exposed administrative interfaces, unreferenced backup files, and HTTP method testing.
- **[Identity-Management-Testing](Identity-Management-Testing/)** (`WSTG-IDNT`): Role definitions, user registration workflows, account provisioning, and username enumeration.
- **[Authentication-Testing](Authentication-Testing/)** (`WSTG-ATHN`): Default credentials, brute-force resilience, password reset flaws, and multi-factor authentication bypasses.
- **[Authorization-Testing](Authorization-Testing/)** (`WSTG-ATHZ`): Directory traversal, horizontal/vertical privilege escalation, and Insecure Direct Object References (IDOR).
- **[Session-Management-Testing](Session-Management-Testing/)** (`WSTG-SESS`): Session token generation, JWT weaknesses, Cross-Site Request Forgery (CSRF), and session invalidation.
- **[Injection-Testing](Injection-Testing/)** (`WSTG-INPV`): SQL/NoSQL injection, Stored/Reflected XSS, XML External Entity (XXE) injection, SSTI, and command injection.
- **[Error-Handling](Error-Handling/)** (`WSTG-ERRH`): Stack trace exposure, verbose database errors, and improper exception handling.
- **[Weak-Cryptography](Weak-Cryptography/)** (`WSTG-CRYP`): Weak encryption/hashing algorithms, hardcoded cryptographic secrets, and insecure token encoding.
- **[Business-Logic-Testing](Business-Logic-Testing/)** (`WSTG-BUSL`): Price/quantity manipulation, workflow circumvention, and anti-automation bypasses.
- **[Client-side-Testing](Client-side-Testing/)** (`WSTG-CLNT`): DOM-based XSS, open redirects, client-side validation bypasses, CORS misconfigurations, and WebSockets.
- **[API-Testing](API-Testing/)** (`WSTG-APIT`): REST/GraphQL endpoint enumeration, mass assignment, and improper API rate limiting.

## WSTG Reporting Template Structure

Each finding follows the official OWASP WSTG test case structure defined in [FINDING_TEMPLATE.md](FINDING_TEMPLATE.md):

1. **Metadata**: WSTG ID, Category, Target Endpoint, CWE / OWASP Top 10 mapping, Severity, and Challenge Name.
2. **Summary**: Overview of the vulnerability or security mechanism and its impact.
3. **Test Objectives**: Specific goals and security controls evaluated during testing.
4. **How to Test**:
   - **Black-Box Testing**: External reconnaissance, probing, and proof-of-concept steps.
   - **Gray-Box / Source Code Review**: Client-side JavaScript bundle (`main.js`) or configuration analysis.
5. **Remediation**: Architectural and code-level controls required to resolve the issue.
6. **Tools**: Testing tools used during the assessment.
7. **References**: Links to corresponding OWASP WSTG sections and documentation.

## References

- [OWASP Web Security Testing Guide (WSTG)](https://owasp.org/www-project-web-security-testing-guide/)
- [OWASP Juice Shop Official Project](https://owasp.org/www-project-juice-shop/)
- [Pwning OWASP Juice Shop Companion Guide](https://pwning.owasp-juice.shop/)
