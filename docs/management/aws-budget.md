# AWS Budget and Usage Rules

**Version:** 0.1 · **Status:** Draft (GestC01)

## 1. Situation
Each AWS lab has **$50**. Several labs will be used to separate **QA** and **Production**. Once a lab's budget is spent, that lab can no longer be used.

## 2. Restrictions to verify
If the labs are **AWS Academy Learner Lab** (confirm with the instructor), public documentation indicates the following:

- Only the **us-east-1** and **us-west-2** regions can be used.
- IAM users and roles cannot be created; the existing **LabRole** is used.
- Credentials are temporary and expire when the session ends (about 4 hours).
- There are limits such as a maximum of 32 vCPUs and EBS volumes of up to 100 GB.
- The budget indicator is not updated in real time; do not push it to the limit.

All of this constrains Terraform and the architecture. It must be confirmed in the actual lab during GestC05–06.

## 3. Lab allocation (template)
| Lab | Environment | Purpose | Budget | Owner |
|---|---|---|---|---|
| Lab A | QA | Development, integration and testing | $50 | (to be completed) |
| Lab B | QA (reserve) | Load testing | $50 | (to be completed) |
| Lab C | Production | Final demonstration | $50 | (to be completed) |

Adjust to the labs available. Rule: Production is only deployed from GestC15; before that it consumes the minimum.

## 4. Cost estimate per resource
Calculate each resource with the **AWS pricing calculator** and fill in the table. No figures are included here because they depend on region and configuration.

| Resource | Quantity | Estimated hours/month | Estimated cost | Environment |
|---|---|---|---|---|
| EC2 instances (services) | | | | |
| Load balancer | | | | |
| Bastion | | | | |
| Database | | | | |
| Queues, SNS, Lambda | | | | |
| S3 (frontend and files) | | | | |
| Data transfer | | | | |

## 5. Cost-saving rules
1. Shut down or destroy resources at the end of each work session (`terraform destroy` for anything ephemeral).
2. Check each lab's spending **every week** and record it in the table below.
3. Watch for resources that bill by the hour even when unused (load balancers, NAT Gateway, databases, running instances).
4. Short, planned load tests, with notice to the team.
5. One person responsible per lab.

## 6. Weekly tracking
| Week | Lab | Cumulative spend | % of budget | Notes |
|---|---|---|---|---|
| | | | | |
