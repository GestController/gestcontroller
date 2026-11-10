# Scope Charter

**Project:** GestController · **Version:** 0.1 · **Status:** Draft (GestC01)

## 1. Purpose
Build a platform that controls who can enter each area of a hospital, at what time and under what conditions, with an auditable trail of every access.

## 2. General objective
Deliver, within 4 months, a microservices platform deployed with Terraform on AWS (QA and Production environments) that manages identities, permissions and access events, with real-time monitoring.

## 3. Specific objectives
- Manage identities, roles and permissions by area, schedule and context.
- Decide accesses online and record every decision with its reason.
- Apply CQRS and an event-driven architecture with queues, DLQ and resilience patterns.
- Automate the credential lifecycle with n8n.
- Deploy as code (Terraform) to QA and Production within the AWS labs budget.
- Validate performance with load tests (k6).

## 4. Scope
**Included**
- Monorepo with services, web dashboard (React + Vite) and infrastructure as code.
- Core services: identity, access policies, access control and events.
- Door and reader simulator instead of real hardware.
- Web dashboard hosted on S3, with real-time events over WebSocket.
- Documentation, tests and manuals.

**Excluded (future work)**
- Biometrics and real physical readers.
- AI, agents and MCP; data platform (data lake).
- Kubernetes orchestration.

## 5. Deliverables
Code in the monorepo, Terraform infrastructure, documentation in `/docs`, test report (including load tests), manuals and final report.

## 6. Assumptions and constraints
- Duration: 4 months (November 2026 to March 2027), weekly sprints.
- Each AWS lab has $50. The budget is limited and cannot be extended.
- The team is small; some weeks have reduced capacity because of the end-of-year holidays.
- Lab restrictions (available services, regions, permissions) shape the architecture.

## 7. Success criteria
- An allowed access and a denied access work end to end in QA.
- Every decision is recorded and visible on the dashboard in real time.
- The QA and Production deployments can be reproduced with Terraform.
- Load tests meet the thresholds defined in the test plan.
- No lab exceeds its budget.

## 8. Milestones
| Milestone | Target date |
|---|---|
| Base design and documentation approved | Dec 8, 2026 |
| Monorepo, CI and base Terraform operational | Dec 22, 2026 |
| Core services running in QA | Jan 26, 2027 |
| Dashboard on S3 with real time | Feb 2, 2027 |
| Load and resilience tests | Feb 16, 2027 |
| Production deployed and project closed | Mar 9, 2027 |
