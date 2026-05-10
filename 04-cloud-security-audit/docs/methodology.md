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

