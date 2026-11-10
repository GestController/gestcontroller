# Technical Topics Matrix

Each topic the team must consider is assigned to a document and an implementation sprint.
Topics marked (?) need clarification before a decision is made (see the final section).

| Topic | What is documented | Document | Sprint |
|---|---|---|---|
| Monorepo | Folder structure and dependency rules | architecture/monorepo-nx-turborepo.md | GestC05 |
| Nx and Turborepo | Comparison and tool decision (ADR-0001) | architecture/monorepo-nx-turborepo.md | GestC05 |
| Microservices | Services, responsibilities and communication | architecture/overview.md | GestC03 |
| CQRS architecture | Command model and read model | architecture/patterns-and-resilience.md | GestC09 |
| Event-driven | Event catalog, broker, consumers | architecture/patterns-and-resilience.md | GestC10 |
| Use of views | Read views (read models) in the database | architecture/patterns-and-resilience.md | GestC11 |
| Queues | Event and job queues | architecture/patterns-and-resilience.md | GestC10 |
| DLQ | Dead-letter queue and reprocessing | architecture/patterns-and-resilience.md | GestC10 |
| Circuit breaker | Protection of calls between services | architecture/patterns-and-resilience.md | GestC13 |
| "Transaction alone" (?) | Consistency between database and events (outbox) | architecture/patterns-and-resilience.md | GestC13 |
| Use of hash / consistent hashing | Load distribution and hashing of credentials and audit | architecture/patterns-and-resilience.md | GestC11 |
| WebSocket | Real-time events to the dashboard | architecture/frontend.md | GestC12 |
| Frontend on S3 | Static hosting of the React + Vite dashboard | architecture/frontend.md | GestC12 |
| Rendering | CSR vs SSR and decision (ADR-0004) | architecture/frontend.md | GestC12 |
| Dynamic pages | Dynamic routes and data in a SPA | architecture/frontend.md | GestC12 |
| AWS Labs | Restrictions, budget and usage rules | management/aws-budget.md | GestC01 |
| Load balancer | Balancing, TLS and routing | architecture/aws-infrastructure.md | GestC06 |
| Security through the load balancer | Security groups and minimal exposure | architecture/aws-infrastructure.md | GestC06 |
| Bastion | Administrative access to private resources | architecture/aws-infrastructure.md | GestC06 |
| Lambda functions | Use cases (pre-signed URL, DLQ reprocessing) | architecture/aws-infrastructure.md | GestC10 |
| Pre-signed URL | File upload and download on S3 | architecture/aws-infrastructure.md | GestC12 |
| n8n | Automation workflows (onboarding, offboarding, alerts) | architecture/aws-infrastructure.md | GestC09 |
| DevOps | Workflow, CI/CD and environments | devops/ci-cd.md | GestC05 |
| Terraform | Modules and QA and Production environments | devops/terraform-and-environments.md | GestC06 |
| Project value in prod and QA (?) | Configuration and cost per environment | devops/terraform-and-environments.md | GestC06 |
| k6 | Massive load testing | testing/test-plan.md | GestC13–14 |
| "OpenCore or Hermes" server (?) | To be clarified | (to be defined) | (to be defined) |

## Topics to clarify

1. **"OpenCore or Hermes" server:** what role does it play in the project (application server, engine, other)?
2. **"Transaction alone":** assumed to mean transactional consistency between database and events. Is that right, or does it mean something else (transaction isolation, sagas)?
3. **"Project value in prod and QA":** assumed to mean configuration and cost of each environment. Does it mean some other value?
4. **"Use of hash":** two uses are covered (hashing of credentials and audit, and consistent hashing). Which one is required?
