# REST API Security Testing Methodologies

> Authoring and integrating modern REST API vulnerability assessment protocols for the OWASP Web Security Testing Guide (WSTG).

---

## Overview

This project documents my architectural and technical contributions to the WSTG `12-API_Testing` directory (Issue #492 / PR #1427). The objective was to migrate core assessment methodologies from legacy cheat sheets into the modern WSTG modular framework. This required writing new content to strict OWASP Style Guide standards (active voice, second-person instruction), resolving GitHub Actions CI/CD parsing failures, and passing rigorous `markdownlint-cli2` checks.

---

## Key Highlights

- **API Reconnaissance:** Engineered methodology for intercepting and analyzing hidden REST parameters, explicitly pivoting WSTG focus from legacy formats toward modern OpenAPI/Swagger specifications.
- **Excessive Data Exposure:** Formulated precise testing guidance for Mass Assignment vulnerabilities via request body manipulation and JSON payload injection.
- **Broken Function Level Authorization (BFLA):** Enhanced the HTTP Methods section with targeted execution strategies for HTTP Verb Tampering assessments.
- **CI/CD & Governance Compliance:** Resolved pipeline linting failures and standardized technical terminology across the repository (e.g., standardizing "api" to "API" and "Regex" to "Regular expression") to secure a clean merge into the `master` branch.

---

## Links

Here are the links to the upstream WSTG contribution:
* [OWASP WSTG Pull Request #1427](https://github.com/OWASP/wstg/pull/1427): The officially merged PR integrating these methodologies into the OWASP `master` branch.
* [Study of API Testing Issue #492](https://github.com/OWASP/wstg/issues/492): The underlying architectural issue this contribution resolved.

---

## Contact

For any questions or feedback, reach out:  
**Paarth Pandey**  
[LinkedIn](https://www.linkedin.com/in/paarth-pandey-13779529b/) | [GitHub](https://github.com/paarthpandey10) | paarthdxb@gmail.com

---

> Author: [Paarth Pandey](https://github.com/paarthpandey10)
>  
> OWASP Foundation Contribution
