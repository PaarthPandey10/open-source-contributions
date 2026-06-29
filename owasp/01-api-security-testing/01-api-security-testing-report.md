# Implementation Report: REST API Security Testing Methodologies

> An architectural and technical report documenting the migration, modernization, and CI/CD compliance of REST API testing protocols for the OWASP Web Security Testing Guide (WSTG).

---

## Overview

This report provides a comprehensive narrative of my contributions to the OWASP Web Security Testing Guide (WSTG). It follows the end-to-end engineering workflow: adopting the long-standing "Study of API Testing" objective (Issue #492), proposing a structured integration plan, and executing Pull Request #1427. The core objective was to extract REST-specific methodologies from legacy cheat sheets, modernize the attack vectors, and successfully merge the artifacts into the `master` branch of the OWASP repository.

---

## Phase 1: Architecture & Content Migration

Following guidance from the WSTG maintainers, the approach focused exclusively on enhancing the newly modularized Section 4.12 (`12-API_Testing`) directory. The core REST assessment methodologies were migrated directly from the legacy `REST_CS_Migrate.md` cheat sheet. 

The modifications targeted three primary vulnerability verticals:

*   **API Reconnaissance (`01-API_Reconnaissance.md`):** Integrated methodology for intercepting and analyzing hidden REST parameters. The content explicitly shifted focus to emphasize modern OpenAPI/Swagger specifications over legacy formats.
*   **Excessive Data Exposure (`03-Testing_for_Excessive_Data_Exposure.md`):** Added explicit testing guidance for Mass Assignment vulnerabilities. The methodology detailed execution via request body manipulation.
*   **Broken Function Level Authorization (`04-API_Broken_Function_Level_Authorization.md`):** Enhanced the HTTP Methods section. Included specific execution methodologies for HTTP Verb Tampering.

---

## Phase 2: Governance & CI/CD Pipeline Resolution

To ensure a clean merge into the upstream `OWASP:master` branch, the raw technical content required strict alignment with OWASP's automated governance pipelines and style guides.

### 1. WSTG Style Guide Compliance
All migrated content was completely rewritten to adhere to the strict WSTG Style Guide. This included enforcing active voice, maintaining second-person instruction, and eliminating zero-tolerance forbidden abbreviations. Local validations were executed and passed using `markdownlint-cli2`.

### 2. Resolving Automated Pipeline Linting
During the remote PR validation phase, the `github-actions` bot flagged formatting constraints. The `04-API_Broken_Function_Level_Authorization.md` file failed the `MD007/ul-indent` rule. The unordered list indentation was corrected from 2 spaces to the strictly required 4 spaces to clear the CI block.

### 3. Terminology Standardization
The OWASP automated terminology checks identified legacy nomenclature within `01-API_Reconnaissance.md`. To align with global repository standards, "Regex" was corrected to "Regular expression", and lowercase "api" instances were capitalized to "API". 

---

## Phase 3: Upstream Integration

After resolving all markdown linting and terminology errors via a secondary commit, the GitHub Actions pipeline passed all checks. 

The contribution resulted in 22 additions and 6 deletions across 3 files. The 2 commits were officially approved and merged into the `OWASP:master` repository.

### External Links & References

*   **OWASP WSTG Pull Request:** [Enhance REST API Testing Methodologies #1427](https://github.com/OWASP/wstg/pull/1427)
*   **Underlying Architecture Issue:** [Study of API Testing #492](https://github.com/OWASP/wstg/issues/492)

---

## Contact

For any questions or feedback, reach out:  
**Paarth Pandey**  
[LinkedIn](https://www.linkedin.com/in/paarth-pandey-13779529b/) | [GitHub](https://github.com/paarthpandey10) | paarthdxb@gmail.com

---

> Author: [Paarth Pandey](https://github.com/paarthpandey10)
>  
> OWASP Foundation Contribution
