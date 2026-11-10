# CI/CD and DevOps Workflow

**Version:** 0.1 · **Status:** Draft (GestC05)

## 1. Continuous integration (GitHub Actions)
On every pull request:
1. Install dependencies and use the monorepo cache.
2. Run only what is affected: lint, tests and build.
3. Validate Terraform (`fmt` and `validate`) without cloud credentials.
4. Check that there are no secrets in the code.

## 2. Deployment
Lab credentials are temporary, so a fully automatic deployment from GitHub is not practical. Therefore:
- **QA:** semi-automatic deployment, with the owner running `terraform apply` and deploying the services with freshly renewed credentials.
- **Production:** manual, controlled deployment in GestC15.
- Service images or packages are versioned with the commit tag.

## 3. Environments and branches
| Branch | Environment | Rule |
|---|---|---|
| `main` | QA | Team-agreed protection; only enters through a reviewed PR |
| Version tag | Production | Created by hand after QA tests pass |

## 4. Basic observability
Structured logs per service, a correlation identifier per request and basic metrics (latency, errors, queue and DLQ size).
