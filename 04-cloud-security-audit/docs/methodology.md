# Cloud Security Audit Methodology

## Project Title

**Cloud Security Audit With Prowler: From Findings to Risk-Based Remediation**

## Purpose

The purpose of this project is to perform a practical AWS cloud security audit using Prowler and document the full audit lifecycle from preparation to remediation.

This project is not focused only on running an automated scanner. The main goal is to demonstrate how security findings can be reviewed, prioritized, documented, remediated, and retested in a professional cloud security workflow.

The audit focuses on:

- Separating meaningful security risks from low-value noise
- Prioritizing findings based on risk and context
- Documenting accepted risks
- Creating a remediation roadmap
- Producing both executive and technical security documentation

## Audit Scope

The audit will be performed in a personal AWS account created and controlled by the project owner.

The scope includes the following AWS security areas:

- Identity and Access Management
- Root account security
- IAM users and MFA status
- IAM password policy
- Access key hygiene
- S3 bucket security
- CloudTrail and logging configuration
- Security group exposure
- Encryption and versioning gaps where safe to test

The audit will follow this lifecycle:

```text
Prepare → Scan → Analyze → Report → Remediate → Retest

## Environment

The audit will be performed in a personal AWS account created and controlled by the project owner.

A personal AWS account was selected for the final portfolio project because it provides full control over IAM, S3, CloudTrail, security groups, and other AWS services needed for a realistic audit.

A sandbox environment is safer for practice, but it may restrict IAM creation and limit the number of meaningful findings. Since this project focuses on controlled misconfigurations, remediation, and retesting, a personal AWS account is more suitable.

No production workloads, customer data, or sensitive files will be used in this environment.

## Cost Controls

This project is designed to remain near-zero or zero cost.

To avoid unnecessary AWS charges, the following resources will not be created:

- EC2 running instances
- RDS databases
- NAT Gateways
- Load balancers
- SageMaker resources
- Bedrock resources
- GPU instances
- Managed Grafana or Prometheus
- SMS alerts

Only safe and low-cost configurations will be used. Any temporary test resources created for the audit will be removed or remediated after testing.

Before creating intentional misconfigurations, the following safety checks will be completed:

- Confirm root account MFA is enabled
- Confirm an AWS budget alert is configured
- Use an IAM admin user instead of the root account
- Avoid uploading real or sensitive data
- Keep all test resources clearly named and documented

## Assumptions

This audit is based on a personal AWS account used only for learning and portfolio purposes.

The following assumptions apply:

- The AWS account does not contain production workloads
- No customer or business-sensitive data is stored in the account
- Any insecure configurations are intentionally created for testing
- Misconfigurations will be remediated after the audit
- Findings will be reviewed based on context, not severity alone
- The goal is to demonstrate security judgment, not just tool usageest
