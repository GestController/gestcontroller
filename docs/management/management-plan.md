# Management Plan

| | |
|---|---|
| **Project** | GestController |
| **Jira task** | SCRUM-10 · GestC01 - Develop a management plan (schedule, roles, risks) |
| **Version** | 0.2 (draft for review) |
| **Date** | November 2026 |
| **Related documents** | `scope-charter.md`, `risk-register.md`, `aws-budget.md`, `git-jira-conventions.md` |

## 1. Purpose

This plan describes how the GestController project is organized, scheduled and controlled over its 4 months: who does what, when, with which tools, and how progress, risks, cost and changes are managed.

## 2. Approach and tools

| Aspect | Decision |
|---|---|
| Methodology | Scrum with **1-week sprints** (Tuesday to Tuesday) |
| Planning and tracking | Jira (space `SCRUM`): backlog, board, timeline and sprint reports |
| Code and documents | One private GitHub monorepo (`gestcontroller`); everything enters through pull requests |
| Link between tools | The Jira key (`SCRUM-n`) in branches, commits and pull request titles |
| Cloud | AWS labs ($50 each), one for QA and one for Production, managed with Terraform |
| Team communication | (to be completed: chat group and meeting channel) |
| Language | All project artifacts are written in English |

## 3. Schedule

Duration: **November 10, 2026 to March 9, 2027** (17 sprints). Sprint names in Jira follow the pattern `GestCnn - Name`.

| Sprint (name in Jira) | Dates | Goal | Main deliverables |
|---|---|---|---|
| GestC01 - Scope and management plan | Nov 10–17 | Define scope and plan | Scope document, management plan, conventions, `/docs` structure |
| GestC02 - Requirements and roles | Nov 17–24 | Define what to build | Requirements specification, roles and permissions matrix |
| GestC03 - Use cases and architecture | Nov 24–Dec 1 | Define how it works | Use cases, architecture overview, ADR-0004 and ADR-0005 |
| GestC04 - Data, API and testing | Dec 1–8 | Close the design | Data model, API contracts, test plan, ADR-0002 and ADR-0003 |
| GestC05 - Monorepo and CI | Dec 8–15 | Prepare the repository | Monorepo tooling (ADR-0001), base CI |
| GestC06 - Terraform and QA base | Dec 15–22 | Prepare the infrastructure | Terraform base, QA network, load balancer and bastion, ADR-0006 |
| GestC07 - Review (holidays) | Dec 22–29 | Light load | Document review and adjustments |
| GestC08 - Identity service (holidays) | Dec 29–Jan 5 | Light load | identity-service |
| GestC09 - Policies and n8n | Jan 5–12 | Policies and automation | access-policy-service (CQRS), n8n onboarding/offboarding flows |
| GestC10 - Access control and queues | Jan 12–19 | Access decision and events | access-control-service, queues, DLQ, Lambda |
| GestC11 - Events and views | Jan 19–26 | Event recording | access-event-service, read views, hashing |
| GestC12 - Dashboard on S3 | Jan 26–Feb 2 | User interface | React + Vite dashboard on S3, WebSocket, pre-signed URL |
| GestC13 - Resilience and k6 | Feb 2–9 | Reliability | Circuit breaker, outbox, first k6 tests |
| GestC14 - QA deployment and load | Feb 9–16 | Full QA validation | Complete QA deployment, load test results |
| GestC15 - Production and security | Feb 16–23 | Production | Production deployment, security review |
| GestC16 - Manuals and test report | Feb 23–Mar 2 | Documentation | Installation guide, user manual, test report |
| GestC17 - Closing | Mar 2–9 | Close the project | Final report, demo, retrospective |

**Notes**
- Sprints GestC07 and GestC08 coincide with the end-of-year holidays: no critical tasks are planned.
- Check other public holidays (for example Carnival in February) and adjust that week's capacity.
- **Critical path:** open ADRs closed by GestC05 → Terraform QA by GestC06 → core services by GestC11 → full QA validation by GestC14 → Production by GestC15.

## 4. Roles and responsibilities

| Role | Responsibilities | Person |
|---|---|---|
| Technical lead / architecture | Technical decisions, ADRs, pull request reviews, scope control | (to be completed) |
| Infrastructure and DevOps | Terraform, AWS labs, CI/CD, cost control | (to be completed) |
| Backend services | Microservices, events, unit and integration tests | (to be completed) |
| Frontend | React + Vite dashboard | (to be completed) |
| Quality and documentation | Test plan, k6, `/docs`, review of deliverables | (to be completed) |

A person may hold more than one role. Each role has a backup so work does not depend on a single person.

### Responsibility matrix (R = does the work, A = accountable, C = consulted, I = informed)

| Activity | Tech lead | Infra/DevOps | Backend | Frontend | Quality/Docs | Instructor |
|---|---|---|---|---|---|---|
| Scope and requirements | A | C | C | C | R | I |
| Architecture and ADRs | A/R | C | C | C | C | I |
| Terraform and AWS | C | A/R | C | I | I | I |
| Microservices | A | C | R | C | C | I |
| Dashboard | C | I | C | A/R | C | I |
| Tests and k6 | C | C | R | R | A | I |
| Documentation | C | C | C | C | A/R | I |
| Budget control | C | A/R | I | I | I | I |

## 5. Work management

### 5.1 Workflow
`To do` → `In progress` → `Done`. A task moves to **Done** only when its pull request is merged and its acceptance criteria are met.

### 5.2 Task standard
Every task has: a verb-based title in English, a short description, acceptance criteria, an assignee, a label with the sprint code (for example `GestC01`) and a type label, a story point estimate and, when it applies, a due date.

### 5.3 Estimation
Story points (1, 2, 3, 5). **No task above 3 points:** larger tasks are split into subtasks. Capacity per sprint is calibrated after the first two sprints.

### 5.4 Definition of Ready
- Clear title and acceptance criteria.
- Estimated and assigned.
- Dependencies identified.

### 5.5 Definition of Done
- Code or document merged through a reviewed pull request.
- Commit and pull request include the Jira key.
- Tests pass in CI (when applicable) and documentation is updated.
- No credentials or secrets in the repository.

## 6. Ceremonies

| Ceremony | Duration | When | Purpose |
|---|---|---|---|
| Sprint planning | 15 min | First day of the sprint | Choose the tasks for the week |
| Quick check-in | 10 min | Mid-week | Find blockers |
| Sprint review and retrospective | 15 min | Last day of the sprint | Review the result and decide improvements |

At the end of each sprint, the team writes one line on what went well and one on what to change.

## 7. Communication and reporting

| What | Frequency | Channel | Audience |
|---|---|---|---|
| Board and sprint report | Every sprint | Jira | Team |
| Progress update to the instructor | Every two weeks (to be agreed) | Meeting or message | Instructor |
| Technical decisions | When made | ADRs in `docs/architecture/decisions/` | Team and instructor |
| AWS spending | Weekly | Table in `aws-budget.md` | Team |
| Risks | Every two weeks | `risk-register.md` | Team |

## 8. Quality and documentation management

- All documents are Markdown in `/docs` and change only through reviewed pull requests.
- The status table in `docs/README.md` is updated whenever a document is finished.
- Test levels and thresholds are defined in `testing/test-plan.md`.
- At least one reviewer other than the author for every pull request.

## 9. Budget and resource management

- Each AWS lab has $50 and cannot be extended.
- One person is responsible for each lab and records its spending every week.
- Resources are shut down or destroyed at the end of each session. Load tests are planned and announced.
- Alert threshold: when a lab reaches **70%** of its budget, the technical lead reviews usage and decides what to cut.

## 10. Risk management

Risks are recorded in `risk-register.md` with probability, impact, score, mitigation, trigger and owner. The register is reviewed every two weeks and whenever a risk materializes. High-score risks (score 6 or more) are discussed at the next planning.

## 11. Change control

1. Anyone can request a change by creating a Jira task of type *change request*.
2. The technical lead assesses its impact on scope, schedule, cost and risk.
3. Changes that affect scope or milestones need the instructor's agreement.
4. If approved, the scope document, this plan and the Jira backlog are updated, and the version number is incremented.

## 12. Progress metrics

| Metric | Source | Target |
|---|---|---|
| Points completed vs planned per sprint | Jira sprint report | 80% or more |
| Open tasks carried over to the next sprint | Jira | Decreasing trend |
| AWS spending per lab | `aws-budget.md` | Under 100%, review at 70% |
| Open high-score risks | `risk-register.md` | Decreasing trend |
| Pending ADRs | `decisions/README.md` | None after GestC06 |

## 13. Document history

| Version | Date | Change |
|---|---|---|
| 0.1 | November 2026 | Initial draft |
| 0.2 | November 2026 | Expanded for SCRUM-10: roles matrix, work management, communication, change control, metrics |
