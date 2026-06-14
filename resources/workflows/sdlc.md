# Software Development Lifecycle (SDLC) — Nouf Squad

This document defines the 5-Phase Software Development Lifecycle (SDLC) pipeline. It provides a standardized guide for the Nouf Squad to safely and predictably move tasks from requirements through design, code, auditing, and production release.

---

## 🔄 Pipeline Overview

```
[Phase 1: Alignment] ──> [Phase 2: Design] ──> [Phase 3: Dev] ──> [Phase 4: Audit] ──> [Phase 5: Release]
 (Joker, PM, Mizan,   (Designer, Tariq, Head  (Backend/Frontend  (Rex, Hakim, Nashbah, (Joker, User, DevOps,
   Product Analyst)    of Design, UI/UX, PM)   Engineers, TL)       QA, Pen-Tester)         SRE, Data)
```

---

## 📋 Phase 1: Planning & Business Alignment

> **Primary Roles:** Product Manager (PM) · **Auditor:** Mizan (Business Thinker / CEO) · **Supporting:** Product Analyst, Joker

### Entry Criteria
*   New feature request or issue submitted by the User.
*   Initial specifications or business goals outlined.

### Activities
*   **PRD Mapping:** PM writes the Product Requirements Document (PRD) and defines user stories with explicit acceptance criteria.
*   **Monetization & Leakage Audit:** Mizan reviews the plan to ensure no payment channels are bypassed, transaction paths are secure, and business logic aligns with the revenue model.
*   **KPI Review:** Product Analyst defines the telemetry and analytics hooks to track feature performance.

### Exit Criteria
*   Requirements finalized, ticket created, and approved by PM and Mizan.

---

## 🎨 Phase 2: Design & Architecture

> **Primary Roles:** Head of Design, Tariq (Solution Architect) · **Supporting:** UI Designer, UX Designer, PM

### Entry Criteria
*   Approved ticket/PRD from Phase 1.

### Activities
*   **UX/UI Mockups:** UX Designer maps out user journeys and navigation wireframes. UI Designer creates style assets, choosing palettes, spacing variables, and enforcing Right-to-Left (RTL) compatibility. Head of Design signs off on HIG standards.
*   **Technical Architecture:** Tariq designs schemas, drafts endpoints, and writes an **Agent Decision Record (AgDR)** for any structural or data change.

### Exit Criteria
*   Figma / design guidelines finalized.
*   AgDR written and signed off by Tariq (saved under `docs/agdr/`).

---

## 🛠️ Phase 3: Code Implementation (Build)

> **Primary Roles:** Backend Engineer, Frontend Engineer · **Coordinator:** Tech Lead (TL) · **Standards:** Head of Engineering

### Pre-Build Gates (Mandatory)
Before coding begins, the implementing engineer must verify:
*   A ticket exists with clear checkboxes for acceptance criteria.
*   An approved AgDR is referenced (if database or API schemas are changing).

### Single-Ticket Constraint
Engineers must work on exactly **one ticket at a time** on a dedicated feature branch.
```
WRONG:
  Start #12 --> Start #13 --> Start #14 --> PR with all changes combined

RIGHT:
  Start #12 --> PR --> Review --> Merge
  Start #13 --> PR --> Review --> Merge
```

### Database Migration Sub-Workflow
Migrations have a high blast radius and are strictly gated:
1.  **Migration Ticket:** A separate ticket labelled `migration` must exist.
2.  **Migration AgDR:** Tariq and DevOps must approve a rollback strategy and downtime estimate.
3.  **Local Test:** Local schema changes must be applied and rolled back successfully before committing.

### Exit Criteria
*   Feature branch implements the exact acceptance criteria.
*   Code compiles and runs without warnings locally.

---

## 🔍 Phase 4: Auditing & QA Verification

> **Primary Roles:** Rex (Code Reviewer), Hakim (Security Auditor), Nashbah (QA Auditor) · **Supporting:** QA Engineer, Penetration Tester

### Entry Criteria
*   Pull Request (PR) opened.
*   CI/CD pipeline builds cleanly.

### Activities
*   **Code Review (Rex):** Automated review of code conventions, formatting, naming, and TypeScript syntax.
*   **Security Audit (Hakim & Pen-Tester):** Hakim scans packages for vulnerabilities, checks secrets leaks, and audits RLS rules. Penetration Tester runs exploit diagnostics on new API endpoints.
*   **QA & Visual Audit (Nashbah & QA Engineer):** QA Engineer runs unit/integration test suites. Nashbah runs dynamic visual E2E tests, verifying layout responsiveness and RTL styling.
*   **Anti-Stale Testing Gate:** Nashbah enforces state transition checks. If a test script performs an action (e.g., clicking a button) but the page state remains identical without verifying the target change (modal popup, URL change, reload), the audit **MUST FAIL**.

### Exit Criteria
*   Approved reviews from Rex, Hakim, and Nashbah.
*   Code coverage targets met (minimum 80%).

---

## 🚀 Phase 5: User Approval & Release

> **Primary Roles:** Joker (Orchestrator), Platform Engineer (DevOps) · **Supporting:** Site Reliability Engineer (SRE), Data Engineer, User

### Entry Criteria
*   All audits in Phase 4 passed.

### Activities
*   **Release Report:** Joker compiles task metrics, test results, and token costs into a `release_report_[task]_[date].md` file at the root.
*   **User Approval:** Joker presents the report summary in chat and awaits the User's approval.
*   **Deployment:** Upon approval, DevOps runs schema migrations, merges the code to `main`, and deploys the build.
*   **Monitoring:** SRE monitors application logs, error rates, and CPU/memory utilization. Data Engineer verifies data ingestion pipelines are active.

### Exit Criteria
*   Clean release report compiled.
*   User approves merge.
*   Build is live in production and verified.

---

## 🛑 Global safety gates
*   **3 Re-work Attempts:** If any task or check fails an audit or compile gate, the squad is limited to 3 re-work attempts. On the 3rd failure, the session halts and escalates to the User.
*   **30-Second Timeout:** All terminal commands must return output or verify status within 30 seconds to prevent resource loops.
