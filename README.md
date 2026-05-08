# Cloud Security Portfolio

A growing collection of production-grade cloud security projects designed to demonstrate real-world cloud security skills. These projects go beyond tutorials to showcase the thinking, trade-offs, and decision-making that define professional cloud security work.

This portfolio focuses on practical cloud security problems such as secure file sharing, cloud misconfiguration detection, container security, secrets hygiene, logging, monitoring, and incident-ready architecture.

The goal is not only to show that the projects work, but to explain why each security decision was made.

---

## Why These Projects Matter

The cloud security market has matured. Employers are no longer impressed by tool lists or certifications alone. They want evidence that you understand real systems, real risks, and real trade-offs.

These projects are designed to mirror how cloud security is practiced in the real world:

- They show that security decisions are based on risk, not guesswork
- They demonstrate understanding of scale, access control, monitoring, and response
- They prove that technical work can be explained clearly
- They show the ability to build, document, test, and improve cloud security controls

If even a few projects are completed at this depth, they will carry more weight than many shallow labs.

---

## Projects Overview

| # | Project | Domain | Key Skills Demonstrated | Status |
|---|---|---|---|---|
| 1 | Secure File Vault | Data Security / IAM | S3 security, KMS encryption, Cognito, IAM roles, CloudTrail, pre-signed URLs | Planned |
| 2 | Cloud Security Scout | Security Automation | Lambda, Python Boto3, EventBridge, DynamoDB, SNS, misconfiguration detection | Planned |
| 3 | Container Security Falcon | Container Security | Docker, ECR scanning, ECS, IAM task roles, CodePipeline, CloudWatch | Planned |
| 4 | Secret Sweep | DevSecOps / Secrets Hygiene | Secret detection, pattern matching, CI/CD security, GitHub Actions | Planned |
| 5 | Centralized Logging Lab | Visibility & Detection | CloudTrail, CloudWatch, log storage, alarms, incident response basics | Future |
| 6 | IAM Least Privilege Lab | Identity & Access Management | IAM roles, policies, MFA, least privilege, access review | Future |
| 7 | Cloud Security Audit | Compliance & Audit | Prowler, risk prioritization, remediation planning, security reporting | Future |
| 8 | Threat Modeling Case Study | Risk Analysis | STRIDE, attack paths, control mapping, security reasoning | Future |

---

## Project 1: Secure File Vault

A secure file-sharing portal for sensitive financial or client information.

### Security Problem

Organizations often need to share sensitive files with clients, employees, or external parties. Without strong access control, encryption, and logging, this can lead to unauthorized access, data exposure, reputational damage, fines, and loss of trust.

### Goal

Build a secure cloud-based file vault where only authorized users can upload, download, and manage files.

### Planned Services and Controls

- Amazon S3 for secure file storage
- AWS KMS for encryption
- IAM roles for viewers, editors, and administrators
- Amazon Cognito for user authentication
- Multi-factor authentication
- Pre-signed URLs for secure downloads
- CloudTrail for access logging
- CloudWatch alarms for suspicious activity
- S3 lifecycle rules for retention and cost control
- AWS Amplify for hosting the user interface

### Security Focus

- Encryption at rest
- Least privilege access
- Temporary credentials
- Role-based access control
- Audit logging
- Secure file sharing
- Retention and lifecycle management

---

## Project 2: Cloud Security Scout

A serverless cloud security scanner that checks AWS resources for common security misconfigurations.

### Security Problem

Cloud environments can grow quickly, making it difficult to manually track insecure configurations across services. Public storage, exposed ports, missing encryption, and weak identity controls can create serious security risks.

### Goal

Create an automated scanner that regularly checks cloud resources against a security baseline and reports risky configurations.

### Planned Checks

- Public S3 buckets
- Security groups exposing sensitive ports
- RDS databases without encryption
- IAM users without MFA
- Unencrypted EBS volumes
- ECR repositories without scan-on-push

### Planned Services and Controls

- AWS Lambda for running security checks
- Python and Boto3 for AWS API interaction
- Amazon EventBridge for scheduled scans
- DynamoDB for storing findings
- SNS or Slack alerts for urgent risks
- CloudWatch metrics and alarms
- Terraform for infrastructure provisioning

### Security Focus

- Misconfiguration detection
- Automated monitoring
- Risk prioritization
- Security visibility
- Continuous improvement

---

## Project 3: Container Security Falcon

A container security project focused on securing container images, deployment pipelines, runtime permissions, and monitoring.

### Security Problem

Containers are often built and deployed quickly, but insecure base images, excessive permissions, weak scanning, and poor monitoring can introduce serious risks into production environments.

### Goal

Build a secure container deployment workflow from image creation to runtime monitoring.

### Planned Services and Controls

- Docker for container image creation
- Minimal base image such as Alpine Linux
- Non-root container user
- Amazon ECR for image storage
- ECR image scanning for vulnerabilities
- AWS CodePipeline for automated build and deployment
- Amazon ECS for container deployment
- IAM task roles with least privilege
- CloudWatch logs, alarms, and dashboards
- Terraform for infrastructure provisioning

### Security Focus

- Image hardening
- Vulnerability scanning
- Least privilege runtime access
- Secure CI/CD
- Runtime monitoring
- Container observability

---

## Project 4: Secret Sweep

A script-based project to detect hard-coded secrets in codebases.

### Security Problem

Developers may accidentally commit API keys, access tokens, passwords, or credentials into source code. Once exposed, these secrets can be abused by attackers and may lead to unauthorized access.

### Goal

Build a simple secret scanning tool that detects exposed secrets before they are pushed into a repository.

### Planned Features

- Pattern matching for common secret formats
- Detection of API keys, tokens, passwords, and credentials
- Clear output showing the file and line where the secret was found
- GitHub Actions integration for CI/CD checks
- Safe test files with fake secrets only

### Security Focus

- Secure coding practices
- DevSecOps basics
- CI/CD security
- Preventing credential leakage
- Early detection before production

---

## Repository Structure

```text
cloud-security-portfolio/
│
├── README.md
│
├── 01-secure-file-vault/
│   ├── README.md
│   ├── architecture/
│   ├── screenshots/
│   ├── terraform/
│   └── docs/
│
├── 02-cloud-security-scout/
│   ├── README.md
│   ├── src/
│   ├── terraform/
│   ├── screenshots/
│   └── findings/
│
├── 03-container-security-falcon/
│   ├── README.md
│   ├── app/
│   ├── Dockerfile
│   ├── terraform/
│   ├── pipeline/
│   └── docs/
│
├── 04-secret-sweep/
│   ├── README.md
│   ├── scanner/
│   ├── tests/
│   └── .github/workflows/
│
└── docs/
    ├── diagrams/
    ├── notes/
    └── learning-log.md
