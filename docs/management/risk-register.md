# Risk Register

| | |
|---|---|
| **Project** | GestController |
| **Jira task** | SCRUM-10 · GestC01 - Develop a management plan (schedule, roles, risks) |
| **Version** | 0.2 (draft for review) |
| **Review frequency** | Every two weeks and whenever a risk materializes |

## 1. Scoring

- **Probability (P):** 1 = low, 2 = medium, 3 = high.
- **Impact (I):** 1 = low, 2 = medium, 3 = high.
- **Score = P × I:** 1–2 low · 3–4 medium · 6–9 high.
- **Status:** Open, Mitigated, Occurred, Closed.

## 2. Summary

| ID | Risk | P | I | Score | Owner | Status |
|---|---|---|---|---|---|---|
| R-05 | Scope too large for 4 months | 3 | 3 | **9** | Technical lead | Open |
| R-01 | Exhausting the budget of an AWS lab ($50) | 2 | 3 | **6** | Infrastructure | Open |
| R-02 | Lab restrictions block part of the architecture | 2 | 3 | **6** | Infrastructure | Open |
| R-03 | Temporary lab credentials expire during a deployment | 3 | 2 | **6** | Infrastructure | Open |
| R-07 | Low-capacity weeks because of holidays | 3 | 2 | **6** | Technical lead | Open |
| R-08 | Dependence on a single person for infrastructure | 2 | 3 | **6** | Team | Open |
| R-09 | Inconsistency between events and data | 2 | 3 | **6** | Backend | Open |
| R-12 | Instructor changes requirements or scope | 2 | 3 | **6** | Technical lead | Open |
| R-06 | Learning curve (CQRS, Terraform, queues) | 2 | 2 | 4 | Technical lead | Open |
| R-10 | Open technical decisions delay sprints | 2 | 2 | 4 | Technical lead | Open |
| R-11 | Accidental push to `main` (private repo without branch protection) | 2 | 2 | 4 | Technical lead | Open |
| R-04 | Loss of the Terraform state or of the lab | 1 | 3 | 3 | Infrastructure | Open |

## 3. Details

| ID | Mitigation | Trigger (early warning) | Contingency |
|---|---|---|---|
| R-05 | Prioritize the end-to-end flow; keep dashboard and n8n as the first things to cut; limit work in progress | Less than 80% of planned points done in two consecutive sprints | Reduce scope with the instructor's agreement; move items to future work |
| R-01 | Weekly spending checks; shut down or destroy resources after each session; avoid unneeded hourly-billed resources; planned load tests | A lab reaches 70% of its budget | Stop non-essential resources; move tests to a lab with remaining budget; reduce environment size |
| R-02 | Verify allowed services and permissions in GestC05–06; keep an alternative per service (see `aws-infrastructure.md`) | A required service or permission is denied in the lab | Switch to the documented alternative (for example RabbitMQ instead of SQS) |
| R-03 | Documented credential renewal procedure; short deployments; CI without cloud credentials | A deployment fails with an authorization or expired-token error | Renew credentials and rerun; split the deployment into smaller steps |
| R-07 | Light-load sprints GestC07 and GestC08; no critical tasks in holiday weeks | Team availability reported below plan | Move tasks to the next sprint; protect the critical path |
| R-08 | Document procedures; pair on infrastructure tasks; rotate lab ownership | One person holds all lab credentials or knowledge | Assign a backup owner and run a shared walkthrough |
| R-09 | Outbox pattern, idempotent consumers, DLQ with alarm | Messages in the DLQ or duplicated records | Reprocess from the DLQ; add reconciliation checks |
| R-12 | Agree scope in writing (`scope-charter.md`); use the change control process; short progress updates every two weeks | New requirements appear after scope approval | Assess impact; trade new items for existing ones |
| R-06 | Short research spikes in GestC03–05; ADRs; pull request reviews | A task exceeds its estimate twice | Simplify the pattern; ask the instructor for guidance |
| R-10 | Close ADRs before GestC05; due date in Jira | An ADR is still open one sprint after its deadline | Technical lead decides and records it; revisit later if needed |
| R-11 | Team agreement: no direct push to `main`; require a review and passing CI; consider making the repository public or upgrading the plan | A commit appears on `main` without a pull request | Revert the commit; remind the team of the agreement |
| R-04 | Backup of the state outside the repository; infrastructure reproducible from code | State file missing or corrupted | Rebuild the environment from Terraform; import existing resources if needed |

## 4. Review log

| Date | Reviewed by | Changes |
|---|---|---|
| November 2026 | (to be completed) | Initial register (R-01 to R-12) |
