# Architecture Decision Records (ADR)

Each important decision is documented with this template in an `ADR-000n-title.md` file.

```
# ADR-000n: Title
Status: Proposed | Accepted | Superseded
Date:
## Context
## Decision
## Alternatives considered
## Consequences
```

## Accepted decisions
| ADR | Topic | Decision |
|---|---|---|
| ADR-0007 | Repository | Single `gestcontroller` monorepo, private; frontend in `apps/web` |

## Pending decisions
| ADR | Topic | Initial proposal | Deadline |
|---|---|---|---|
| ADR-0001 | Monorepo tool (Nx or Turborepo) | Nx | GestC05 |
| ADR-0002 | Backend language and framework | TypeScript (NestJS), to be confirmed | GestC04 |
| ADR-0003 | Messaging (SQS/SNS or RabbitMQ) | SQS + SNS, depending on the lab | GestC04 |
| ADR-0004 | Frontend rendering | CSR (SPA) on S3 | GestC03 |
| ADR-0005 | Behavior on access-decision failures | Deny by default with short TTL | GestC03 |
| ADR-0006 | Terraform state and lab credential handling | Remote state if the lab allows it, backup outside the repo | GestC06 |
