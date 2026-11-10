# Monorepo: Structure and Tooling

**Version:** 0.1 · **Status:** Draft (GestC05) · **Pending decision:** ADR-0001

## 0. Repository
A **single repository** is used, `gestcontroller` (formerly `gestcontroller-backend`), private. It contains the services, the web dashboard, the infrastructure and this documentation. The `gestcontroller-frontend` repository is archived after its contents are migrated to `apps/web`. Decision recorded in ADR-0007.

### Migration from the two repositories
1. Rename `gestcontroller-backend` to `gestcontroller` (Settings → General) and update the local remote: `git remote set-url origin <new-url>`.
2. Change its visibility to private (see the warning about branch protection in `../management/git-jira-conventions.md`).
3. Copy the contents of `gestcontroller-frontend` into `apps/web` (if there is history worth keeping, it can be brought in with `git subtree add`).
4. Add the `docs/` folder and open a pull request with the Jira key.
5. Archive `gestcontroller-frontend` (Settings → Danger Zone → Archive).
6. Check in Jira (GitHub for Atlassian) that the renamed repository is still connected and still links branches, commits and PRs.

## 1. Proposed structure
```
gestcontroller/
├── apps/
│   ├── web/                      React + Vite dashboard
│   ├── identity-service/
│   ├── access-policy-service/
│   ├── access-control-service/
│   └── access-event-service/
├── libs/
│   ├── contracts/                API and event types and schemas
│   ├── auth/                     Authentication and authorization utilities
│   └── observability/            Shared logs and metrics
├── infra/                        Terraform (modules and environments)
├── tests/load/                   Load tests with k6
├── docs/
├── .github/workflows/
└── nx.json  or  turbo.json
```

## 2. Monorepo rules
- Services do **not** import each other; they communicate through APIs or events defined in `libs/contracts`.
- Shared libraries are small and have a clear owner.
- Each service is built, tested and deployed independently.

## 3. Nx and Turborepo
Both tools organize tasks and caching in a monorepo. Normally one of the two is chosen.

| Criterion | Nx | Turborepo |
|---|---|---|
| Dependency graph and "affected only" commands | Yes, very complete | Yes, simpler |
| Generators and templates | Yes | Limited |
| Task caching (local and remote) | Yes | Yes |
| Learning curve | Higher | Lower |
| Fit for several services and libraries | Very good | Good |

**Initial recommendation:** Nx, because of the number of services, the generators and the command to run only what is affected. If the team prioritizes simplicity, Turborepo is a valid alternative. To be closed in ADR-0001 during GestC05.

## 4. Service language
Nx and Turborepo are designed mainly for JavaScript and TypeScript projects. That favors using **TypeScript on the backend** (for example NestJS) in addition to the React dashboard. If Java (Spring Boot) or Python (FastAPI) is kept as proposed earlier, a monorepo is still possible, but these tools add less value. Decision in ADR-0002.
