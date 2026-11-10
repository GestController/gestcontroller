# Requirements

This folder is completed in sprints GestC02 and GestC03.

| Document | Content | Sprint | Status |
|---|---|---|---|
| requirements-specification.md | Functional and non-functional requirements with identifiers | GestC02 | Pending |
| roles-permissions-matrix.md | Roles, areas and permissions (RBAC + attributes) | GestC02 | Pending |
| use-cases.md | Use cases with main and alternative flows | GestC03 | Pending |

## Starting point for the requirements
- **FR-01** Manage staff identities and roles.
- **FR-02** Define permissions by area, schedule and context.
- **FR-03** Evaluate an access request and answer allowed or denied with a reason.
- **FR-04** Record every decision as an auditable event.
- **FR-05** Show events in real time on the dashboard.
- **FR-06** Revoke credentials and propagate the revocation to the services.
- **NFR-01** Availability of the access decision even if secondary services fail.
- **NFR-02** Performance: thresholds defined in `testing/test-plan.md`.
- **NFR-03** Security: least privilege, TLS and no secrets in the repository.
- **NFR-04** Reproducibility: QA and Production deployable with Terraform.
