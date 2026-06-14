# Deployment Process — Nouf Squad

This document details how code is built, promoted through staging, and released into production.

---

## 👥 Deployment Roles

*   **Platform Engineer (DevOps):** Configures CI/CD scripts, manages Infrastructure as Code (IaC), and manages database migration pipelines.
*   **Site Reliability Engineer (SRE):** Monitors server metrics (CPU, latency, logs) post-deploy, verifies health checks, and executes rollback plans in the event of an incident.

---

## 🔄 Deployment Pipeline

```
Commit Merged to main
       │
       ▼
 1. CI/CD Run (Build, Lint, Test, Audit)
       │
       ▼
 2. Deploy to Staging (Apply IaC, deploy services)
       │
       ▼
 3. E2E & Smoke Verification (Nashbah & QA)
       │
       ▼
 4. Release Report & User Approval Gate
       │
       ▼
 5. Promoted to Production (Rollback plan armed)
       │
       ▼
 6. Post-Deploy Monitoring (First 24-48 hours)
```

---

## 📁 Environment Configuration

| Environment | Purpose | Promotion Method |
| :--- | :--- | :--- |
| **Development** | Local implementation and sandbox testing | Manual local execution |
| **Staging** | Pre-production testing, QA audits, and E2E verification | Automated deploy on commit to `main` |
| **Production** | Live system serving users | Manual gate triggered after User approval |

---

## 📋 Pre-Deploy Checklist

Before promoting any build to Production, the DevOps engineer must verify:
- [ ] All automated tests (unit, integration, and E2E) are passing in Staging.
- [ ] The PR has been reviewed and approved by Rex, Hakim, and Nashbah.
- [ ] The database migration ticket has a tested rollback plan.
- [ ] Staging logs show zero active exceptions.
- [ ] The team is online to monitor the deploy (avoid Friday afternoon deployments unless critical).

---

## 🛑 Rollback Procedures

### 1. Code Rollback
If a deployment degrades the live platform, SRE should revert the merge commit immediately:
```bash
# Revert the latest merge commit
git revert -m 1 HEAD
git push origin main
```
The CI/CD pipeline will automatically build and deploy the reverted codebase.

### 2. Infrastructure & Data Rollback
*   If database migrations fail, DevOps must apply the tested rollback SQL commands detailed in the task's Migration AgDR.
*   For server or cloud resources, DevOps must revert the configuration code (IaC) to the last known-good state.

### 3. Rollback Decision Tree
```
Is the issue affecting core transaction paths or user security?
  ├── YES ──► Rollback immediately (<15 mins)
  └── NO  ──► Is performance degraded?
                ├── YES ──► Rollback within 1 hour
                └── NO  ──► Hotfix in next deployment cycle
```

---

## 📊 Post-Deploy Monitoring

The SRE must monitor telemetry at the following milestones:

### First 30 Minutes
*   Track error rates (should be < 1%).
*   Check API latency (p99 latency should stay below 2 seconds).
*   Verify critical user flows (login, payments, and checkout).

### First 24 Hours
*   Review server CPU and memory usage (warn if > 80%).
*   Audit logs for slow-running queries.
*   Track customer support channels for regression reports.
