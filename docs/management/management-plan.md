# Management Plan

**Version:** 0.1 · **Status:** Draft (GestC01)

## 1. Methodology
Scrum with **1-week** sprints (Tuesday to Tuesday), managed in Jira. Code and documents live in GitHub, linked through the Jira key (`SCRUM-n`).

## 2. Ceremonies
| Ceremony | Duration | When |
|---|---|---|
| Planning | 15 min | First day of the sprint |
| Quick check-in | 10 min | Mid-week |
| Review and retrospective | 15 min | Last day of the sprint |

## 3. Schedule (17 sprints)
| Sprint (name in Jira) | Dates | Focus |
|---|---|---|
| GestC01 - Scope and management plan | Nov 10–17 | Scope, management plan, `/docs` structure |
| GestC02 - Requirements and roles | Nov 17–24 | Requirements and roles matrix |
| GestC03 - Use cases and architecture | Nov 24–Dec 1 | Use cases and architecture |
| GestC04 - Data, API and testing | Dec 1–8 | Data model, API contracts, test plan |
| GestC05 - Monorepo and CI | Dec 8–15 | Monorepo (Nx or Turborepo) and base CI |
| GestC06 - Terraform and QA base | Dec 15–22 | Base Terraform and QA environment (network, load balancer, bastion) |
| GestC07 - Review (holidays) | Dec 22–29 | Light load for holidays: review and adjustments |
| GestC08 - Identity service (holidays) | Dec 29–Jan 5 | Light load for holidays: identity-service |
| GestC09 - Policies and n8n | Jan 5–12 | access-policy-service (CQRS) and n8n flows |
| GestC10 - Access control and queues | Jan 12–19 | access-control-service, queues, DLQ and Lambda |
| GestC11 - Events and views | Jan 19–26 | access-event-service, views and hashing |
| GestC12 - Dashboard on S3 | Jan 26–Feb 2 | Dashboard on S3, WebSocket and pre-signed URL |
| GestC13 - Resilience and k6 | Feb 2–9 | Resilience (circuit breaker, outbox) and first k6 tests |
| GestC14 - QA deployment and load | Feb 9–16 | Full QA deployment and load tests |
| GestC15 - Production and security | Feb 16–23 | Production and security (bastion, load balancer) |
| GestC16 - Manuals and test report | Feb 23–Mar 2 | Manuals and test report |
| GestC17 - Closing | Mar 2–9 | Closing: final report, demo, retrospective |

Check public holidays (end of year and Carnival) and adjust the capacity of those weeks.

## 4. Roles
| Role | Responsibilities | Person |
|---|---|---|
| Technical lead / architecture | Decisions, ADRs, PR review | (to be completed) |
| Infrastructure and DevOps | Terraform, AWS labs, CI/CD | (to be completed) |
| Backend services | Microservices, events, tests | (to be completed) |
| Frontend | React + Vite dashboard | (to be completed) |
| Quality and documentation | Test plan, k6, `/docs` | (to be completed) |

## 5. Definition of Done
- Code or document merged into the repository through a reviewed PR.
- Commit and PR include the Jira key.
- Tests pass in CI (when applicable) and documentation is updated.
- No credentials or secrets in the repository.

## 6. Control
- Jira board, sprint reports and epic timeline.
- Weekly tracking of AWS spending (see `aws-budget.md`).
- Risks reviewed every two weeks (see `risk-register.md`).
