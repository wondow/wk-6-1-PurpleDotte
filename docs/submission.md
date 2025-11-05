# 📤 Submission Guidelines — Book Store App QA Project

## 📦 Weekly Submissions
All groups submit the full repository weekly for continuous progress and feedback.

### Week 1: Initial Setup & Planning (Due: Wednesday, Nov 5, 2025)
- Repo runs locally (`npm install`, `npm start`)
- Project board (Jira/GitHub Projects) created and shared
- `tests/test-plan.md` (use template below)
- Team roles and communication plan

### Week 2: Test Design & Early Execution (Due: Tuesday, Nov 11, 2025)
- Draft test cases/checklists in `tests/test-cases.md` (use template below)
- Early manual/automated scripts (optional)
- Initial defect log in `tests/defect-log.md` (use format below)

### Week 3: Test Execution & Reporting (Due: Tuesday, Nov 18, 2025)
- Executed results (manual/automated) with evidence
- Updated defect log with severity/priority and attachments
- Screenshots/videos/logs of key issues

## 🏁 Final Submission (Due: Tuesday, Nov 18, 2025)
- `tests/final-report.md` (executive summary, approach, environment, results, defect analysis, risks, recommendations)
- Jira/Project exports or screenshots (board, filters, dashboards)
- All code and documentation committed
- 5-minute video presentation link (see `docs/video-guide.md`)
## 🧩 Templates
### 📝 Test Plan (tests/test-plan.md)

# RAID Team Comprehensive Test Plan

**Project:** Book Store App — Web Application QA Project  
**Team Name:** RAID  
**Testing Period:** November 5, 2025 – November 18, 2025 (3 Weeks)

## Team Roles

| Role | Name | Core Responsibility |
|------|------|---------------------|
| Test Manager | Dennis | Planning, Schedule, Final Report Sign-off |
| Risk Analyst | Cindy | Risk-Based Prioritization, Defect Triage (Severity/Priority) |
| Test Executer | Deborah | Test Design, Execution, Evidence Capture |

## 1. Objective and Scope

### 1.1 Test Objective

The primary goal is to provide comprehensive quality assurance by verifying the application against all requirements and identifying defects in the following areas:

- **Functional Correctness:** Catalog, Cart/Checkout, Payments, Orders, Admin.
- **Accessibility (FR-X01):** Ensure compliance with WCAG 2.1 AA.
- **Performance (FR-X02):** Meet LCP and TTI budgets.
- **Security Hygiene (FR-X04):** Verify UGC sanitization and URL scheme validation.

### 1.2 In-Scope Features (Traceability to FR Codes)

| Component | Key Functional Requirements (FR) | Execution Priority |
|-----------|----------------------------------|-------------------|
| Discovery | Search, Filter, Sort | Verify AND filter logic and stable sorting. |
| Checkout Flow | FR-O01, FR-O02 | Test all four steps (Shipping → Review → Payment → Confirmation). |
| Payments | FR-O03 | Paystack integration, currency validation (NGN/GHS/USD/ZAR). |
| Orders/Admin | FR-O04, FR-M03 | Order Status transitions (Pending → Paid → Delivered); Admin access guard. |

### 1.3 Out-of-Scope Items

Real backend services, real payment capture, multi-currency catalog display, and jurisdiction-specific tax/shipping logic.

## 2. Environments and Tools

| Category | Environment/Tool | Constraint/Target | Role Responsibility |
|----------|------------------|-------------------|---------------------|
| Project Management | Jira Cloud or GitHub Projects | Must use defined Components, Labels (intentional-defect, a11y, perf), and Workflow. | Dennis |
| Testing Environment | Local Repo with npm start | Requires pk_test_... key and REACT_APP_CURRENCY set (NGN, GHS, USD, or ZAR). | Deborah |
| Browsers/Devices | Latest 2 releases of Chrome, Firefox, Safari, Edge | Must validate Mobile, Tablet, and Desktop breakpoints (FR-X03). | Deborah |
| Accessibility Tools | axe DevTools, WAVE, NVDA/JAWS/VoiceOver | Verify WCAG 2.1 AA compliance. | Deborah |
| Performance Tools | Lighthouse, PageSpeed Insights | Measure LCP (≤2.5s/3s) and TTI (≤1s) (FR-X02). | Deborah |
| Admin Access | localStorage | Set app.user to { role: 'admin' } to access /admin. | Deborah |

## 3. Test Strategy and Risk Analysis

### 3.1 Test Strategy

The team will use a Risk-Based Testing (RBT) strategy, prioritizing execution based on the P1 items in the backlog and the inherent risk of the intentional defects.

### 3.2 Risk Prioritization (Cindy - Risk Analyst Focus)

| Risk Area | Impact / Requirement | Mitigation Strategy | Priority Target |
|-----------|---------------------|---------------------|-----------------|
| Intentional Defects | 10 known complex defects (e.g., Rounding ±0.01, Day 8 return, A11y modal) must be explicitly found and logged. | Dedicated Test Cases: Cindy must ensure specific test cases are created for all 10 defects, tracked with the intentional-defect label. | High |
| Checkout Flow Blockers | Failure in Payments (FR-O03) or the 4-step wizard (FR-O02) blocks the core transaction. | P1 Execution: Maximize test coverage on the /checkout route and Paystack integration; ensure proper error handling and status updates. | Critical |
| Security/UGC | Unsanitized UGC (Reviews/Q&A) could allow XSS attacks (FR-S01). | Negative Testing: Test input fields with scripts and non-whitelisted URL schemes (javascript:) to verify sanitation is enforced. | High |

## 4. Project Schedule and Criteria

### 4.1 Weekly Milestones

| Week | Due Date | Key Activities | Required Deliverables |
|------|----------|----------------|----------------------|
| Week 1 | Nov 5 (Wednesday) | Kickoff, Jira/Board Setup, Environment check. | Signed-off Test Plan. |
| Week 2 | Nov 11 (Tuesday) | Test Case Design, P1 Execution, Defect Triage. | Draft Test Cases (tests/test-cases.md), Interim defect log. |
| Week 3 | Nov 18 (Tuesday) | Full Execution, Defect re-testing, Final Report preparation. | Final Submission (Report, Video link, Board Exports). |

### 4.2 Entry and Exit Criteria

| Criteria Type | Condition |
|---------------|-----------|
| Entry Criteria (Execution Start) | The app runs locally; Jira/GitHub Projects board is configured and shared; Test Plan is signed off. |
| Exit Criteria (Completion / Submission) | Full test execution coverage of P1 items achieved; All defects are logged with full details and evidence; All final artifacts prepared. |

## 5. Required Deliverables and Templates

### 5.1 Bug Report Template (Deborah - Test Executer)

All defects must be logged in the project board using the following mandatory fields:

| Field | Requirement | Definition Source |
|-------|-------------|-------------------|
| Summary | Concise, descriptive title | jira-setup.md |
| Description | 1. Numbered Steps to Reproduce. 2. Expected Result. 3. Actual Result | submission.md |
| Severity/Priority | Critical, Major, Minor, Cosmetic / High, Medium, Low | jira-setup.md |
| Component | Catalog, Checkout, Payments, A11y, Performance, etc. | jira-setup.md |
| Labels | Use intentional-defect, a11y, security as appropriate | jira-setup.md |
| Attachments | Screenshots/videos/logs (Required for Major/Critical) | submission.md |

### 5.2 Final Submission Artifacts (Dennis - Test Manager)

Dennis is responsible for compiling these files by the Nov 18 deadline:

- `team-RAID_final-report.md`
- `team-RAID_presentation.(link or file)` (5-minute video following video-guide.md outline)
- Executed Test Cases, Environment Notes, Accessibility/Performance findings with metrics (LCP, TTI).
- Jira/Project Exports/Screenshots (Bugs by Severity, Heat Map by Component).

## 6. Test Plan Approval and Sign-Off

This section confirms that the Test Plan has been reviewed and approved, authorizing the RAID team to begin the Test Execution phase.

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Test Manager | Dennis | (DK) | (Target: Nov 5, 2025) |
| Risk Analyst | Cindy | NC | (Target: Nov 5, 2025) |
| Test Executer | Deborah | DG | (Target: Nov 5, 2025) |
| Project Lead/Stakeholder | (To be confirmed) | (Must Sign) | (Target: Nov 5, 2025) |




### ✅ Test Case (tests/test-cases.md)

 ## Project Management

The RAID team uses Jira Cloud for project management and issue tracking.

**Board Details:**
- **Platform:** Jira Cloud
- **Project Name:** Book Store App - RAID Team QA
- **Board URL:** https://bgrkaris05-1762159814901.atlassian.net/jira/software/c/projects/BSAQTR/boards/34[]
- **Access:** Dennis (Manager), Cindy (Risk Analyst), Deborah (Test Executer), Instructor
- **Status:** Week 1 - Board created and accessible ✓

Board setup screenshot: `evidence/week1-jira-board.png`evidence/week1-jira-board.png`<img width="1366" height="639" alt="Screenshot 2025-11-05 153957" src="https://github.com/user-attachments/assets/dad3b82b-9cac-4a66-a157-267892f7ecf7" />


Full board configuration and issue creation and test cases will begin in week two


- ID: TC-<area>-<number>

- Title: Concise scenario name
- Pre-conditions: State, user role, data
- Steps:
  1. …
  2. …
- Expected Result: Observable outcomes (UI text, URL, ARIA, network where applicable)
- Post-conditions: State changes
- Evidence: Screenshot/gif paths

### 🐞 Bug Report (defect log entry)
- ID: BUG-<area>-<number>
- Summary: Clear, action-oriented title
- Severity/Priority: (Critical/Major/Minor) / (High/Medium/Low)
- Environment: Browser, version; OS/device; network
- Affected FR(s): e.g., FR-O02
- Steps to Reproduce: Numbered
- Expected Result: …
- Actual Result: …
- Attachments: Paths to screenshots/videos
- Notes: Workarounds, scope of impact

## 📚 Required Artifacts
- Test plan, test cases, defect logs
- Environment notes (browser versions, devices)
- Accessibility/performance findings with metrics (LCP, TTI) and tools used
- CSV exports or screenshots from management tool

## 🗂️ File Naming
- `team-<name>_final-report.md`, `team-<name>_presentation.(mp4|link)`, etc.
- Include team name and date on first page of all documents

## 🏆 Grading Rubric (Guidelines)
- Testing Thoroughness (35%): coverage, depth, negative paths, a11y/perf checks
- Documentation Quality (25%): clarity, structure, evidence, traceability to FR codes
- Video Presentation (20%): concise, insightful, well-evidenced
- Project Management (15%): organized board, statuses, filters/dashboards
- Team Collaboration (5%): roles, consistency, communication

## 📜 Policies
- Late submissions: per course policy (confirm with instructor)
- Academic integrity: cite sources; individual contributions documented
- Privacy: redact keys; do not expose production credentials

## 🎥 Presentation Checklist
- 5 minutes max; follow `video-guide.md`
- 2–3 top defects with evidence and impact
- Include a11y/perf highlights (metrics, tools)
- Recommendations aligned to risk



