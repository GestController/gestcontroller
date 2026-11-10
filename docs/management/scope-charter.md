# Scope and Objectives Document

| | |
|---|---|
| **Project** | GestController |
| **Jira task** | SCRUM-9 · GestC01 - Draft scope and objectives document |
| **Version** | 0.2 (draft for review) |
| **Date** | November 2026 |
| **Author(s)** | (to be completed) |
| **Reviewer** | (to be completed) |

## 1. Background and purpose

Hospitals need to control which staff members can enter each area (emergency rooms, medication storage, equipment rooms, data centers), at what time and under what conditions. Doing this with keys or simple cards leaves no reliable audit trail, and granting or revoking permissions is slow.

GestController is an intelligent platform for managing identities, permissions and physical access events. Its purpose is to decide each access request using explicit rules, record every decision with its reason, and show events in real time.

The project is built as a **monorepo of microservices**, deployed with **Terraform** on **AWS** in two environments (QA and Production), within a **4-month** schedule (November 2026 to March 2027) and a limited cloud budget ($50 per AWS lab).

## 2. Objectives

### 2.1 General objective
Deliver a microservices platform that manages identities, permissions and access events, deployed as code on AWS (QA and Production), with real-time monitoring and documented resilience and load behavior.

### 2.2 Specific objectives

| ID | Objective | How it is measured | Target sprint |
|---|---|---|---|
| O1 | Manage identities, roles, areas, schedules and permissions | The services expose APIs to create and query them | GestC08–09 |
| O2 | Decide each access request and record the decision with its reason | An allowed and a denied request work end to end and produce events | GestC10–11 |
| O3 | Apply CQRS and an event-driven architecture with queues and DLQ | A failed message reaches the DLQ and can be reprocessed | GestC10 |
| O4 | Automate the credential lifecycle with n8n | Offboarding a person revokes their credentials through a workflow | GestC09 |
| O5 | Show access events in real time on a web dashboard hosted on S3 | The dashboard receives events over WebSocket | GestC12 |
| O6 | Deploy QA and Production reproducibly with Terraform | An environment is created from code and destroyed without manual steps | GestC06 / GestC15 |
| O7 | Validate resilience and load behavior | k6 results and resilience tests documented against the thresholds in the test plan | GestC13–14 |
| O8 | Keep the cost within the labs' budget | No AWS lab exceeds $50 | Continuous |
| O9 | Document the project completely, in English | All documents in `/docs` reviewed through pull requests | GestC17 |

## 3. Scope

### 3.1 In scope

| Area | Included |
|---|---|
| Repository | One private monorepo (`gestcontroller`) with services, dashboard, infrastructure and documentation |
| Services | identity-service, access-policy-service, access-control-service, access-event-service |
| Architecture | Microservices, CQRS, events, queues, DLQ, circuit breaker, outbox, read views |
| Access control | Role- and attribute-based rules (RBAC + ABAC), deny by default |
| Devices | A door and reader **simulator** (no physical hardware) |
| Frontend | React + Vite dashboard on S3, with real-time events (WebSocket) |
| Automation | n8n workflows for onboarding, offboarding and alerts |
| Infrastructure | Terraform modules; AWS network, load balancer, bastion, queues, Lambda, S3 |
| Quality | Unit, integration, end-to-end, resilience and load tests (k6) |
| Documentation | Management, requirements, architecture, DevOps, testing and manuals |

### 3.2 Out of scope (future work)

| Item | Reason |
|---|---|
| Biometrics and real physical readers | Needs hardware and special data protection treatment |
| AI, agents and MCP | Not required for the core flow; limited time |
| Data platform (data lake) | Not required for the core flow; limited time |
| Kubernetes orchestration | Too costly and complex for the lab budget |
| Integration with real hospital systems | No real institution involved in this phase |

## 4. Deliverables

| Deliverable | Description | Sprint | Acceptance criterion |
|---|---|---|---|
| Project documentation | `/docs` structure and management documents | GestC01–04 | Merged through reviewed pull requests |
| Monorepo and CI | Repository structure and base pipeline | GestC05 | Pull requests run lint, tests and build |
| QA infrastructure | Terraform base for QA | GestC06 | Created and destroyed from code |
| Core services | The four services with tests | GestC08–11 | End-to-end flow works in QA |
| Dashboard | React + Vite app on S3 | GestC12 | Shows events in real time |
| Resilience and load results | Resilience tests and k6 reports | GestC13–14 | Thresholds met or deviations justified |
| Production deployment | Production environment | GestC15 | Deployed from the same Terraform code |
| Manuals and test report | Installation guide, user manual, test report | GestC16 | Reviewed by the team and the instructor |
| Final report and demo | Closing deliverables | GestC17 | Presented to the instructor |

## 5. Stakeholders

| Stakeholder | Interest | Involvement |
|---|---|---|
| Instructor | Accepts the project and evaluates deliverables | Reviews scope, milestones and final results |
| Development team | Designs, builds and documents | All project tasks |
| Hospital security staff (target users) | Needs reliable access control and audit | Represented through use cases and simulated data |

## 6. Assumptions, constraints and dependencies

**Assumptions**
- The team has enough availability for weekly sprints; some weeks in December and January will have reduced capacity.
- The AWS labs remain available for the whole project.

**Constraints**
- Duration: 4 months (17 weekly sprints, November 10, 2026 to March 9, 2027).
- Budget: $50 per AWS lab; the budget cannot be extended.
- Lab restrictions (available services, regions, IAM permissions, temporary credentials) shape the architecture. To be verified in GestC05–06.
- Everything is written in English: documentation, Jira items and commit messages.

**Dependencies**
- Instructor approval of this scope.
- Access to the AWS labs and to the GitHub organization and Jira space.

## 7. Success criteria

The project is considered successful if:
1. An allowed and a denied access request work end to end in QA, and each produces an auditable event.
2. Events appear on the dashboard in real time.
3. QA and Production can be created from Terraform.
4. Resilience and load tests behave as described in the test plan.
5. No lab exceeds its budget.
6. Documentation is complete and in English.

## 8. Milestones

| Milestone | Target date |
|---|---|
| Base design and documentation approved | December 8, 2026 |
| Monorepo, CI and base Terraform operational | December 22, 2026 |
| Core services running in QA | January 26, 2027 |
| Dashboard on S3 with real time | February 2, 2027 |
| Load and resilience tests complete | February 16, 2027 |
| Production deployed and project closed | March 9, 2027 |

## 9. Main risks

The full list is in `risk-register.md`. The most important ones for scope:
- Scope too large for 4 months. Mitigation: prioritize the end-to-end flow and cut the dashboard or n8n before tests and documentation.
- Lab restrictions block part of the architecture. Mitigation: verify services early and keep alternatives (see `../architecture/aws-infrastructure.md`).
- Budget exhausted in a lab. Mitigation: weekly spending checks and shutting down resources (see `aws-budget.md`).

## 10. Approval

| Name | Role | Date | Approval |
|---|---|---|---|
| (to be completed) | Instructor | | |
| (to be completed) | Team representative | | |
