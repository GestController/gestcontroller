# ADR-0007: Single private repository (monorepo)

Status: Accepted
Date: November 2026

## Context
The GitHub organization had two repositories, `gestcontroller-backend` and `gestcontroller-frontend`. The project was conceived as a monorepo with microservices, Terraform infrastructure and documentation.

## Decision
Use a single repository, `gestcontroller` (renaming `gestcontroller-backend`), with `apps/web` for the frontend, `infra/` for Terraform and `docs/` at the root. Archive `gestcontroller-frontend`. The repository will be private.

## Alternatives considered
- Two repositories (backend and frontend): the monorepo would only cover the backend and the documentation would be separate from the frontend.

## Consequences
- One place for code, infrastructure and documentation; a single CI configuration.
- Coordinated changes across services and dashboard in one pull request.
- Being private, on a free plan the automatic protection of `main` is lost (see `../../management/git-jira-conventions.md`).
