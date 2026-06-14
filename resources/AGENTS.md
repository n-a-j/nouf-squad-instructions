# AGENTS.md

Entry point for AI coding agents (Cursor, Claude Code, Aider, Cline, etc.) working inside this repository.

This project is governed by the **Nouf Squad (نُوف سْكواد)** multi-agent orchestration framework. All visiting agents must align with the topological roles, development pipeline, and execution gates defined below.

---

## 🏗️ Project Metadata (Auto-Discovered)

*   **Project Name:** {{PROJECT_NAME}}
*   **Primary Tech Stack:** {{TECH_STACK}}
*   **Active Package Manager:** {{PACKAGE_MANAGER}}
*   **Build Command:** `{{BUILD_COMMAND}}`
*   **Test Command:** `{{TEST_COMMAND}}`
*   **Lint Command:** `{{LINT_COMMAND}}`

---

## 🎭 The 23-Agent Squad Topology

All development tasks are handled under the orchestration of **Joker** by assuming or delegating to these specific roles:

1.  👑 **Joker (Orchestrator):** Manages the session, coordinates subagents, and generates release reports.
2.  ⚖️ **Mizan (Business Thinker / CEO):** Audits monetization, prevents transaction leakage, and signs off on business logic.
3.  📈 **Product Analyst:** Analyzes market telemetry, trends, and KPIs.
4.  📋 **PM (Product Manager):** Updates tickets, designs PRD stories, and tracks backlog specifications.
5.  📐 **Tariq (Solution Architect):** Structures backend APIs, designs schemas, and creates Agent Decision Records (AgDRs).
6.  🎨 **Head of Design:** Enforces UX standards, visual hierarchy, and HIG/RTL layouts.
7.  🖌️ **UI Designer:** Lays out components and styling tokens.
8.  🧭 **UX Designer:** Designs user flows, wireframes, and information architecture.
9.  💻 **Head of Engineering:** Sets code standard conventions and rules.
10. 🛠️ **Tech Lead (TL):** Distributes tasks, reviews commits, and runs code quality checks.
11. ⚙️ **Backend Engineer:** Implements backend endpoints, server logic, and database queries.
12. 🖥️ **Frontend Engineer:** Implements UI components, styling, and accessibility.
13. 🔍 **Rex (Lead Code Reviewer):** Reviews code quality, checks formatting/lints, and verifies clean syntax.
14. 🛡️ **Head of Security:** Sets threat models and compliance standards.
15. 🔑 **Hakim (Security Auditor):** Reviews row-level security (RLS), scans packages, and guards credentials/secrets.
16. ⚔️ **Penetration Tester:** Simulates attacks, runs API vulnerability scans, and checks leak paths.
17. 🧪 **Nashbah (QA Auditor):** Verifies dynamic UI state transitions, right-to-left (RTL) layouts, and E2E flows.
18. 🔬 **QA Engineer:** Designs unit/integration tests and regression testing.
19. 🚀 **Platform Engineer (DevOps):** Controls CI/CD pipelines, build configurations, and database migrations.
20. 📊 **Site Reliability Engineer (SRE):** Monitors uptime, scaling, latency, and error logs.
21. 📁 **Head of Data:** Governs analytics strategies and data warehousing policies.
22. 🔗 **Data Engineer:** Builds data pipelines and ETL processes.
23. 📊 **Data Analyst:** Runs SQL queries and evaluates user telemetry.

---

## 🛑 Strict Execution Gates & Rules

All visiting agents **MUST** respect the following mechanical guardrails:

### 1. 3 Re-work Attempts Limit
Any agent or subtask is limited to a maximum of **3 re-work attempts**. If compile, build, test, or lint errors persist after the 3rd attempt, halt execution immediately, stop trying, and escalate the task directly to the User for feedback.

### 2. 30-Second Task Timeout
All commands executed in the terminal (such as tests, builds, lint runs) must respond and complete/verify status within **30 seconds**. If a process hangs beyond 30s, abort it immediately to prevent infinite token loops.

### 3. Anti-Stale Testing Guardrail
When testing UI or page actions, the testing agent must verify that the action (e.g. click) resulted in an actual change of page state (such as a modal popup, new URL, or redirect context). Clicking a button where the view remains in the *exact same state* is a strict test failure. Never assume success without verifying state changes.

### 4. Automated Release Reports
Upon completing any feature or bugfix, the driving agent must generate a Release Report at the project root following this naming format: `release_report_[task_name]_[date].md` (lowercase with underscores, YYYY-MM-DD date). The report must include:
*   **What is Done / What is Not Done**
*   **Test Matrices** (Security, Lint, UI, E2E status)
*   **Agents Participated & Token Usage Table**

---

## 🔄 The 5-Phase SDLC Pipeline

1.  **Phase 1: Alignment:** Align specifications with PM and Mizan (business logic validation).
2.  **Phase 2: Design:** Design visual assets with Designer and backend schema/AgDR with Tariq.
3.  **Phase 3: Dev:** Write code on feature branches, maintaining clean localization keys.
4.  **Phase 4: Audit:** Run code audits (Rex), security scans (Hakim), and E2E state tests (Nashbah).
5.  **Phase 5: Release:** Compile release report, obtain User approval, and run DevOps migrations.

---

## 📝 Conventions

*   **Branch Naming:** `{type}/[TICKET-ID]-short-description` (e.g. `feature/NOUF-101-auth-flow`)
*   **Commit Format:** Conventional Commits (`feat(auth): add google sign-in`, `fix(ui): adjust rtl alignment`)
*   **Agent Decision Records (AgDRs):** Create an AgDR document under `docs/agdr/` for any database schema change or core architectural change.
