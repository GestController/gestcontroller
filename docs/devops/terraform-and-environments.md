# Terraform and Environments (QA and Production)

**Version:** 0.1 · **Status:** Draft (GestC06)

## 1. Structure
```
infra/
├── modules/
│   ├── network/        Network, subnets, security groups
│   ├── alb/            Load balancer
│   ├── compute/        Service instances
│   ├── database/       Database
│   ├── messaging/      Queues, SNS and DLQ
│   ├── lambda/         Functions
│   ├── s3-frontend/    Dashboard bucket
│   └── bastion/        Administrative access
└── envs/
    ├── qa/             main.tf, variables.tf, terraform.tfvars
    └── prod/           main.tf, variables.tf, terraform.tfvars
```
The modules are the same; only each environment's values change.

## 2. Values per environment
| Value | QA | Production |
|---|---|---|
| AWS lab | Lab A (and B for load) | Lab C |
| Instance size | Minimum sufficient | To be defined in GestC14 |
| Instances per service | 1 | To be defined |
| Log retention | Short | Longer |
| High availability | No | Only if the budget allows |
| Domain and certificate | If the lab allows it | If the lab allows it |

This is the assumed reading of "project value in prod and QA" (see `../topics-matrix.md`).

## 3. Several labs with Terraform
Each lab is a separate account. A **profile** is configured per lab (`lab-qa`, `lab-prod`) and each environment uses its own in the AWS provider.

## 4. Lab particularities
If they are AWS Academy Learner Labs (to be confirmed):
- **IAM:** roles cannot be created; Terraform must **reference** the existing role (LabRole) instead of creating it.
- **Temporary credentials:** renewed every session (about 4 hours) and copied into the local profile. Never committed to the repository.
- **Regions:** us-east-1 or us-west-2.
- Some services may be limited; see alternatives in `../architecture/aws-infrastructure.md`.

## 5. Terraform state
- The state file contains sensitive data: **it is not committed to Git**.
- Preferred option: remote state in S3 inside the lab, if possible.
- Alternative: local state with a backup outside the repository.
- Recorded in ADR-0006.

## 6. Workflow
1. Renew the lab credentials.
2. `terraform fmt` and `terraform validate`.
3. `terraform plan` and review it with another person.
4. `terraform apply` only by an authorized person.
5. When finished, `terraform destroy` anything ephemeral and check spending.
