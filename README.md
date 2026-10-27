# Azure DevOps Infra Pipelines

This repository provides Azure DevOps pipeline templates for Terraform validation, policy checks, and release promotions across Azure landing zones.

## Pipeline architecture

```mermaid
flowchart LR
    A[Pull Request] --> B[Lint & Format]
    B --> C[Terraform Validate]
    C --> D[Policy Scan]
    D --> E[Approval Gate]
    E --> F[Deploy to Environment]
```

## Included templates

- Terraform validation
- Policy and governance checks
- Approval gate and promotion workflow
