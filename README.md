# Cloud Security Portfolio

A growing collection of hands-on cloud security projects focused on secure architecture, identity and access management, automation, monitoring, compliance, and threat-aware cloud design.

This repository is being built as a practical cloud security portfolio. Each project is designed to solve a realistic security problem using cloud-native services, automation, and documented security decisions.

---

## About This Portfolio

Cloud security is not only about knowing tools. It is about understanding risks, designing secure systems, applying least privilege, monitoring activity, and explaining trade-offs clearly.

This portfolio documents my journey of building practical cloud security projects that demonstrate how security controls are applied in real cloud environments.

The goal is to show:

- Secure cloud architecture design
- Identity and access management
- Data protection and encryption
- Monitoring and logging
- Security automation
- Incident detection and alerting
- Infrastructure as Code
- DevSecOps and CI/CD security
- Threat modeling and risk-based thinking

---

## Portfolio Roadmap

| Status | Project | Domain | Key Skills |
|---|---|---|---|
| Planned | Secure File Vault | Data Security / IAM | S3 security, KMS encryption, Cognito, IAM roles, CloudTrail, pre-signed URLs |
| Planned | Cloud Security Scout | Security Automation | Lambda, Python Boto3, EventBridge, DynamoDB, SNS, misconfiguration detection |
| Planned | Container Security Falcon | Container Security | Docker, ECR scanning, ECS, IAM task roles, CodePipeline, CloudWatch |
| Planned | Secret Sweep | DevSecOps / Secure Coding | Secret detection, pattern matching, CI/CD security, GitHub Actions |
| Future | Centralized Logging Lab | Visibility / Detection | CloudTrail, CloudWatch, log storage, alerting |
| Future | IAM Least Privilege Lab | Identity Security | IAM users, groups, roles, policies, MFA |
| Future | Threat Modeling Case Study | Risk Analysis | STRIDE, attack paths, control mapping |

---

## Projects

### 01. Secure File Vault

A secure file-sharing portal for sensitive financial or client information.

**Security problem:**  
Organizations often need to share sensitive files, but weak access control, poor visibility, and lack of encryption can lead to unauthorized access, data leakage, reputational damage, and compliance issues.

**Goal:**  
Build a secure cloud-based file vault where only authorized users can upload, download, and manage files.

**Planned services and controls:**

- Amazon S3 for secure file storage
- AWS KMS for encryption
- IAM roles for viewers, editors, and administrators
- Amazon Cognito for user authentication
- MFA for stronger identity protection
- Pre-signed URLs for secure downloads
- CloudTrail for access logging
- CloudWatch alerts for suspicious activity
- S3 lifecycle rules for retention and cost control
- AWS Amplify for hosting the user interface

**Security focus:**

- Encryption at rest
- Least privilege access
- Temporary credentials
- Role-based access control
- Audit logging
- Secure file sharing
- Retention and lifecycle management

---

### 02. Cloud Security Scout

A serverless cloud security scanner that checks AWS resources for common security misconfigurations.

**Security problem:**  
Cloud environments can grow quickly, making it difficult to manually track insecure configurations across services.

**Goal:**  
Create an automated scanner that regularly checks cloud resources against a security baseline and reports risky configurations.

**Planned checks:**

- Public S3 buckets
- Security groups exposing sensitive ports
- RDS databases without encryption
- IAM users without MFA
- Unencrypted EBS volumes
- ECR repositories without scan-on-push

**Planned services and controls:**

- AWS Lambda for running security checks
- Python and Boto3 for AWS API interaction
- Amazon EventBridge for scheduled scans
- DynamoDB for storing findings
- SNS or Slack alerts for urgent risks
- CloudWatch metrics and alarms
- Terraform for infrastructure provisioning

**Security focus:**

- Misconfiguration detection
- Automated monitoring
- Risk prioritization
- Security visibility
- Continuous improvement

---

### 03. Container Security Falcon

A container security project focused on securing container images, deployment pipelines, runtime permissions, and monitoring.

**Security problem:**  
Containers are often built quickly, but insecure base images, excessive permissions, and weak monitoring can introduce serious risks.

**Goal:**  
Build a secure container deployment workflow from image creation to runtime monitoring.

**Planned services and controls:**

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

**Security focus:**

- Image hardening
- Vulnerability scanning
- Least privilege runtime access
- Secure CI/CD
- Runtime monitoring
- Container observability

---

### 04. Secret Sweep

A script-based project to detect hard-coded secrets in codebases.

**Security problem:**  
Developers may accidentally commit API keys, access tokens, passwords, or credentials into source code.

**Goal:**  
Build a simple secret scanning tool that detects exposed secrets before they are pushed into a repository.

**Planned features:**

- Pattern matching for common secret formats
- Detection of API keys, tokens, passwords, and credentials
- Clear output showing the file and line where the secret was found
- GitHub Actions integration for CI/CD checks
- Safe test files with fake secrets only

**Security focus:**

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
