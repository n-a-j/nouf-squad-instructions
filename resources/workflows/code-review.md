# Code Review Process — Nouf Squad

This document outlines the code review guidelines, roles, and quality standards required to maintain a secure and clean codebase.

---

## 👥 Review Roles

Code review is a collaborative, role-activated workflow:

*   **Author:** The engineer who wrote the code ([Backend Engineer](../roles/engineering/backend-engineer.md) or [Frontend Engineer](../roles/engineering/frontend-engineer.md)). Responsible for self-reviewing and updating the PR.
*   **Rex (Automated Reviewer):** Performs a first-pass review checking code formatting, typescript safety, test coverage, and documentation.
*   **Tech Lead (TL):** Reviews architecture, pattern alignment, and code cleanliness.
*   **Hakim (Security Auditor):** Activates automatically if diffs touch credentials, encryption, authentication (`**/auth/**`), or configuration files (`.env`).
*   **UI Designer:** Reviews layouts, spacing tokens, and RTL design implementation if styling changes are made.

---

## 📋 Author Guidelines

### Before Requesting a Review
1.  **Self-Review:** Read your own code diff line-by-line before opening the PR.
2.  **Verify Tests:** Ensure unit and integration tests run successfully locally.
3.  **Write PR Description:** Document your changes using the layout below.

### PR Description Template
```markdown
## Summary
* Narrative description of what was changed and why. (Avoid short, label-only bullets).

## Testing
* Detailed instructions on how to verify these changes.

Fixes #[Ticket-ID]

---

## Glossary
| Term | Definition |
| :--- | :--- |
| [Term] | [What it means in the context of this PR] |
```

---

## 🔍 Reviewer Guidelines

### Providing Feedback
Reviewers must provide feedback that is constructive, specific, and categorized by severity:

*   `BLOCKING:` A critical issue (e.g., credential leak, security vulnerability, broken business rules) that must be fixed before merge.
*   `SUGGESTION:` A tip or pattern optimization (e.g., "Consider extracting this utility"). Non-blocking.
*   `QUESTION:` Clarifying a design decision.

### Review Checklist

#### 1. Architecture & Patterns (Tariq & Tech Lead)
*   [ ] Does the code align with the approved AgDR?
*   [ ] Are database query modifications optimized (no N+1 queries)?
*   [ ] Is business logic separated from data schemas?

#### 2. Code Quality (Rex & Tech Lead)
*   [ ] Are variables and functions named clearly and descriptively?
*   [ ] Is there any duplicate code (DRY principle)?
*   [ ] Are lints and types resolving cleanly?

#### 3. Security (Hakim & Pen-Tester)
*   [ ] Are inputs validated at the API boundary?
*   [ ] Are credentials and keys protected (no hardcoded secrets)?
*   [ ] Are Row-Level Security (RLS) rules in place for new tables?

#### 4. QA & Visuals (Nashbah & UI Designer)
*   [ ] Do UI changes support Right-to-Left (RTL) locales?
*   [ ] Are spacing variables and color tokens applied correctly?
*   [ ] Do automated tests verify actual state changes (no stale clicks)?

---

## 🛑 Approval & Merge Requirements

Nouf Squad enforces a strict **Two-Marker Merge Gate**:
1.  **Rex & Security Approval:** The code must receive passing reviews from Rex and Hakim.
2.  **CEO/User Sign-off:** The User must review the compiled `release_report.md` and explicitly authorize the merge.

No code may be merged directly to `main` without satisfying both markers.
