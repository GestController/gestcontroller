# Risk Register

**Version:** 0.1 · Probability and impact: High / Medium / Low. Review every two weeks.

| ID | Risk | Prob. | Impact | Mitigation | Owner |
|---|---|---|---|---|---|
| R-01 | Exhausting the budget of an AWS lab ($50) | Medium | High | Weekly spending alerts, shut down resources when finished, avoid unnecessary hourly-billed resources | Infrastructure |
| R-02 | Lab restrictions (unavailable services, IAM permissions, regions) block part of the architecture | Medium | High | Verify allowed services in GestC05–06; keep an alternative per service (see `aws-infrastructure.md`) | Infrastructure |
| R-03 | Temporary lab credentials expire and the deployment fails midway | High | Medium | Documented renewal procedure; short deployments; CI without cloud credentials | Infrastructure |
| R-04 | Loss of the Terraform state or of the lab | Low | High | State backup outside the repository; infrastructure reproducible from code | Infrastructure |
| R-05 | Scope too large for 4 months (CQRS, events, Terraform, frontend, k6) | High | High | Prioritize the end-to-end flow; cut the dashboard or n8n before tests and documentation | Technical lead |
| R-06 | Learning curve (CQRS, Terraform, queues) | Medium | Medium | Short research spikes in GestC03–05; ADRs; PR review | Technical lead |
| R-07 | Low-capacity weeks because of holidays | High | Medium | Light-load sprints GestC07 and GestC08; no critical tasks | Technical lead |
| R-08 | Dependence on a single person for infrastructure | Medium | High | Document procedures and rotate tasks | Team |
| R-09 | Inconsistency between events and data (lost or duplicated messages) | Medium | High | Outbox, idempotent consumers, DLQ with alarm | Backend |
| R-10 | Open technical decisions (pending ADRs) delay sprints | Medium | Medium | Close ADRs before GestC05; due date in Jira | Technical lead |
