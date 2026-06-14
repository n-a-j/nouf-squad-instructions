# Nouf Squad (نُوف سْكواد) Instructions Framework

<p align="center">
  <img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License: MIT">
  <img src="https://img.shields.io/badge/Built%20for-Antigravity%20Orchestrator-007ACC" alt="Built for Antigravity">
  <img src="https://img.shields.io/badge/Compat-Cursor%20%7C%20Claude%20%7C%20Aider%20%7C%20Cline-brightgreen" alt="Compat">
</p>

**The ultimate global multi-agent orchestration framework for autonomous development and strict quality gates.**

Nouf Squad combines the **robust department-based team topologies of ApexYard** with the **strict task-level execution guardrails and safety check loops of Antigravity (Agy)**. Running as a global skill across any project, it auto-discovers configuration settings, auto-generates workspace guidelines, and orchestrates development under a unified 8-agent squad governed by strict re-work and timeout gates.

---

## 📁 What's Inside

```
nouf-squad-instructions/
├── SKILL.md                 # Antigravity skill entry point & ruleset definition
├── README.md                # Framework user handbook (this file)
└── resources/               # All templates — copied to project root during Phase 0
    ├── AGENTS.md            # Entry doc for visiting AI agents (placeholders auto-filled)
    ├── release_report.md    # Task completion & audit verification report template
    ├── onboarding.yaml      # Organization configuration & metadata template
    ├── agdr_template.md     # Agent Decision Record template
    └── workflows/           # Development lifecycle workflows
        ├── sdlc.md          # 5-Phase pipeline: Alignment → Design → Dev → Audit → Release
        ├── code-review.md   # PR quality standards, severity tags, and checklists
        └── deployment.md    # Environment promotion, rollback decision tree, monitoring
```

---

## 🚀 Key Framework Concepts

1. **Phase 0 Project Auto-Discovery:** You don't spend hours explaining your tech stack. The squad automatically scans package files (`package.json`, `Cargo.toml`, `requirements.txt`, etc.) and docs to discover the domain, languages, active tools, and local styles.
2. **Universal AGENTS.md Gate:** Automatically generates and saves a customized `AGENTS.md` file to the root of your project workspace. Any visiting AI agent (Gemini, Claude, Cursor, Aider, Cline) instantly reads this entry file to align with the squad's rules.
3. **8-Agent Hierarchical Squad:** Under **Joker (The Parent Orchestrator)**, 8 specialized agent roles coordinate to manage business strategy (Mizan), technical design (Tariq), coding quality (Rex), security checks (Hakim), quality testing (Nashbah), and platform release (PM, Designer, DevOps).
4. **Strict Execution Safeguards:**
   * **3 Re-work Attempts Limit:** Stops execution and escalates directly to the User if any agent fails an audit 3 times.
   * **30-Second Task Timeout:** Instantly cancels failed terminal commands to prevent infinite token loops.
   * **Anti-Stale Testing:** Rejects testing runs if clicks fail to trigger verified state changes (such as new views or popups).
   * **Consolidated Release Reports:** Automatically writes `release_report_[task_name]_[date].md` with detailed test matrices and token counters.

---

## 🎭 The 23-Agent Squad Matrix

Under the orchestration of **Joker**, the squad is organized into 10 distinct departments mapping all roles from ApexYard to avoid conflicts while incorporating Antigravity's safety gates:

| Department | Agent / Role | Icon | Core Responsibility & Focus |
| :--- | :--- | :---: | :--- |
| **1. Management** | **Joker (Parent Orchestrator)** | 👑 | Spawns subagents, directs the SDLC flow, and compiles Release Reports. |
| **2. Business** | **Mizan (Business Thinker / CEO)** | ⚖️ | Monetization audit, preventing transaction leakage, and business logic sign-off. |
| | **Product Analyst** | 📈 | Market telemetry, competitive analysis, and product metrics tracking. |
| **3. Product** | **Product Manager (PM)** | 📋 | Backlog prioritization, ticket tracking, and PRD/user story specifications. |
| **4. Architecture** | **Tariq (Solution Architect)** | 📐 | API design, database schemas, performance checks, and AgDR generation. |
| **5. Design** | **Head of Design** | 🎨 | Visual design systems, layout consistency, and general HIG standards. |
| | **UI Designer** | 🖌️ | UI styling tokens, color palettes, spacing, and CSS component specifications. |
| | **UX Designer** | 🧭 | Navigation maps, user journey wireframes, and information architecture. |
| **6. Engineering** | **Head of Engineering** | 💻 | Technical standards, syntax patterns, codebase layout, and refactoring guidelines. |
| | **Tech Lead (TL)** | 🛠️ | Task distribution, engineering direction, and peer code reviews. |
| | **Backend Engineer** | ⚙️ | Server-side services, REST/GraphQL endpoints, database queries, and algorithms. |
| | **Frontend Engineer** | 🖥️ | User interfaces, components implementation, responsive CSS, and accessibility. |
| | **Rex (Lead Code Reviewer)** | 🔍 | TypeScript/language clean syntax, lint verification, and pull request reviews. |
| **7. Security** | **Head of Security** | 🛡️ | Threat modeling, security frameworks, and compliance guardrails. |
| | **Hakim (Security Auditor)** | 🔑 | Dependency security updates, RLS reviews, and secret key protection. |
| | **Penetration Tester** | ⚔️ | Simulates API attacks, exploit diagnostics, and interface boundary verification. |
| **8. QA & Testing** | **Nashbah (QA Auditor)** | 🧪 | Dynamic E2E testing, RTL layout verification, and anti-stale UI transitions. |
| | **QA Engineer** | 🔬 | Test suite scripts, unit testing strategies, and manual regression checks. |
| **9. DevOps** | **Platform Engineer (DevOps)** | 🚀 | CI/CD build scripts, automated workflows, and database migration gates. |
| | **Site Reliability Engineer (SRE)** | 📊 | Uptime monitoring, server capacity tracking, latency logs, and scaling. |
| **10. Data** | **Head of Data** | 📁 | Data policies, governance rules, and warehousing patterns. |
| | **Data Engineer** | 🔗 | ETL ingestion pipelines, database schema mappings, and analytics flows. |
| | **Data Analyst** | 📊 | SQL trends exploration, BI dashboard reports, and A/B test analysis. |

---

## 🔄 The 5-Phase SDLC Pipeline

All workspace building and coding operations follow this structured development pipeline:

```
[Phase 1: Alignment] ──> [Phase 2: Design] ──> [Phase 3: Dev] ──> [Phase 4: Audit] ──> [Phase 5: Release]
   (Joker + PM + Mizan)    (Designer + Tariq)    (Dev Subagents)   (Rex + Hakim + Nash)  (Joker + User + DevOps)
```

### 1. Phase 1: Planning & Business Alignment
* **Activities:** PM updates the ticket specifications and PRDs. Mizan audits the planned changes against the business model and ensures no monetization gates or transaction channels are bypassed.
* **Exit Gate:** Verified alignment on requirements.

### 2. Phase 2: Design & Architecture
* **Activities:** Designer lays out the visual specs and styling tokens (supporting right-to-left layout where needed). Tariq designs schemas, drafts Agent Decision Records (AgDRs), and audits database performance.
* **Exit Gate:** Signed-off design specs and approved AgDR.

### 3. Phase 3: Code Implementation
* **Activities:** Joker spawns parallel Dev subagents to implement the feature branch. Coding must utilize localization keys and maintain styled tokens.
* **Exit Gate:** Code builds cleanly without warnings.

### 4. Phase 4: Auditing & QA Verification
* **Activities:** 
  * **Rex** reviews code cleanliness and checks for styling/formatting issues.
  * **Hakim** runs static security scans and audits RLS rules.
  * **Nashbah** runs dynamic UI and E2E checks.
* **Exit Gate:** Zero errors from Rex, Hakim, and Nashbah.

### 5. Phase 5: User Approval & Release
* **Activities:** Joker compiles the final metrics (including token usage and test summaries) into the `release_report.md` and requests User review. Upon approval, DevOps runs migrations and deploys the build.
* **Exit Gate:** Successful deployment.

---

## 🛑 Custom Quality Gates & Safeguards

Nouf Squad implements mechanical gates that protect token usage and ensure software quality:

### 1. 3 Re-work Attempts Limit
If any agent (Dev, Designer, Architect, or Auditor) fails to satisfy an audit criteria or encounters compile issues, they have a maximum of **3 re-work attempts**. If the issue persists on the 3rd attempt, execution is halted immediately, and the task is escalated to the User to prevent looping.

### 2. 30-Second Task Timeout
Terminal commands and background processes must start and complete/respond within a **30-second window**. Commands that hang beyond 30s are terminated immediately, avoiding stalled processes and excessive token consumption.

### 3. Anti-Stale Testing Guardrail
Nashbah verifies actual UI transitions. If a test script clicks a button but the interface remains on the *same page state* without verifying the change (such as a modal appearing, a URL redirecting, or a container reloading), the test is marked as **FAILED**. Stale page transitions are never assumed to be successful.

### 4. Automated Release Report
On task completion, a report named `release_report_[task_name]_[date].md` is saved to the workspace. It documents:
* **Completed Features:** What was added or changed.
* **Out of Scope:** Gaps or deferred tasks.
* **Test Matrix:** Audit results from Rex, Hakim, and Nashbah.
* **Subagents & Token Usage:** A breakdown of active agents and their token consumption.

---

## 🛠️ How to Onboard & Run

### 1. Installation
Ensure the `nouf-squad-instructions` skill is added to your global Antigravity config directory at:
`C:\Users\noufa\.gemini\config\skills\nouf-squad-instructions`

### 2. Run Auto-Discovery (Phase 0)
When you open any project workspace, trigger Phase 0 by prompting:
```text
Nouf Squad, let's run Phase 0 Auto-Discovery on this workspace.
```

The orchestrator will scan your project root, parse your environment configuration, and create two essential workspace files:
* `AGENTS.md` (project-specific guidelines and constraints).
* `onboarding.yaml` (metadata settings for your organization).

### 3. Build Features
To build a new feature or resolve an issue, instruct:
```text
Nouf Squad, let's start a new ticket for [Feature Description].
```
The squad will move through the 5-Phase pipeline, invoking the appropriate agents automatically.

---

## 📝 Customization

You can customize the squad parameters, agent prompts, and gate rules directly in `SKILL.md`. To update onboarding settings, edit the local `onboarding.yaml` file generated at the project root.

---

*Built with passion to bring enterprise-grade multi-agent consistency and safety to solo founders and development squads alike.*
