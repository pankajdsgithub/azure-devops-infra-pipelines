# Architecture

This repository demonstrates a simple Azure DevOps pattern for infrastructure validation without embedding secrets or backend values in source control. The design separates pull-request validation from future environment promotion and keeps all deployment logic intentionally disabled.

## Validation lane

The implemented validation lane covers:

- Terraform formatting checks
- `terraform init` with backend disabled for safe PR validation
- `terraform validate`
- tfsec and Trivy security scans
- placeholder artifact generation only; no real plan file is published for production use

## Future promotion lane

A future promotion lane may be added with:

- environment-specific service connections
- manual approval gates
- artifact consumption for plan review
- deployment only after review and environment readiness checks

This repository does not implement that live deployment lane; the approval template is an example only and remains disabled.

## Governance expectations

The following are recommended governance practices for the real deployment repository, not implemented controls in this reference project:

- Separate dev, QA, and production conventions using environment-specific rules and approvals.
- Use Azure DevOps approvals and environment checks rather than implicit deployment.
- Keep all sensitive values in secret stores and variables at pipeline runtime.
- Prefer least-privilege role assignments for service connections.
- Keep remote-state settings and backend secrets out of source control.
