# Score Board

- **Category:** Information Disclosure / Security through Obscurity
- **Difficulty:** ⭐ (1 Star / Tutorial)
- **Target Endpoint:** `http://localhost:3000/#/score-board`
- **Reference:** [OWASP Juice Shop Companion Guide - Finding the Score Board](https://pwning.owasp-juice.shop/companion-guide/latest/part2/score-board.html)

---

## Purpose of the Web Application Section

This section covers accessing the hidden Score Board, which tracks the user's hacking progress and challenge completion within the OWASP Juice Shop. The objective is to identify and navigate to this unlinked page without direct navigation links provided in the primary user interface.

---

## Considered Approaches

| Approach | Complexity | Time Required | Effectiveness |
| :--- | :--- | :--- | :--- |
| **Predictable URL Guessing** | Low | < 1 minute | **High (Fastest)** |
| **Static Code Analysis (`main.js`)** | Medium | 2–3 minutes | **High (Reliable)** |
| **Automated Endpoint Fuzzing (`ffuf`)** | Medium | 1–2 minutes | **Moderate (Requires SPA filtering)** |

---

## Primary Approach - Guessing the URL

Since most web applications follow predictable naming schemes for their URLs, several intuitive endpoint variations were tested directly in the browser's address bar.

### Tested Candidates
* `scoreboard`
* `scoreBoard`
* `Scoreboard`
* `score-board`

### Result
Access was successfully gained by navigating to:
```
http://localhost:3000/#/score-board
```

### Rationale
This approach was chosen first due to the low complexity of the objective and predictable naming conventions commonly followed by web developers. Attempting high-probability guesses provides an immediate return on effort before investing time into deobfuscating and analyzing source code.

---

## Alternative Approaches

### Alternative Approach 1 - Static Source Code Analysis (`main.js`)

Manually reading minified JavaScript line-by-line is inefficient and time-consuming. However, using Browser Developer Tools with search filters makes static analysis quick and repeatable:

1. Open Browser Developer Tools (`F12`) and navigate to the **Sources** tab.
2. Locate the client-side bundle: `main.js`.
3. Enable **Pretty Print** (`{ }`) to un-minify the code.
4. Search (`Ctrl + F` or `Ctrl + Shift + F`) for route definitions or the keyword `"score-board"`.
5. The Angular routing configuration defines the path explicitly:
   ```javascript
   { path: 'score-board', component: ScoreBoardComponent }
   ```
6. Appending this route fragment to the application base URL (`http://localhost:3000/#/score-board`) loads the component.

---

### Alternative Approach 2 - Automated Discovery Using `ffuf`

Rather than manually guessing endpoints, directory and route fuzzing can be automated using `ffuf` with a standard web discovery wordlist.

#### Command
```bash
ffuf -u http://localhost:3000/FUZZ -w /usr/share/seclists/Discovery/Web-Content/raft-medium-words.txt -mc 200
```

#### SPA Nuance & False Positives
Because OWASP Juice Shop is a Single Page Application (SPA), the web server may return `200 OK` (serving `index.html`) for any arbitrary route. To filter out false positives:
* Measure the standard response byte size of the fallback page.
* Use the `-fs` (filter size) flag in `ffuf` to discard default page matches:
  ```bash
  ffuf -u http://localhost:3000/FUZZ -w /usr/share/seclists/Discovery/Web-Content/common.txt -fs 1024
  ```

---

## Security Assessment & Remediation

### Risk & Vulnerability Analysis
* **Flaw:** Reliance on **Security through Obscurity**.
* **Impact:** Relying on the absence of visible UI navigation links does not secure an endpoint. Anyone performing basic reconnaissance or inspecting client-side bundles can locate and access restricted functionality.

### Remediation
1. **Access Control Enforcement**: If an administrative or sensitive page must be restricted, enforce robust server-side authentication and role-based access control (RBAC). Client-side route hiding is not a security boundary.
2. **Transparent Navigation**: For public-facing functionality intended for users, include direct navigation links in menus rather than leaving unlinked endpoints that invite discovery through fuzzing.