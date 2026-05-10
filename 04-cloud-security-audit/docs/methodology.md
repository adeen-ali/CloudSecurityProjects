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
```

## Environment

The final audit will be performed in a personal AWS account instead of a restricted sandbox environment.

A personal AWS account was selected because this project requires controlled misconfigurations, remediation, and retesting. A sandbox environment is useful for safe practice, but it may restrict IAM creation and reduce the number of meaningful findings that can be tested.

Using a personal AWS account allows the audit to include realistic security scenarios such as IAM users, MFA gaps, password policy weaknesses, CloudTrail configuration, S3 security settings, and security group exposure.

No production workloads, customer data, or sensitive information will be used in this environment.

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
- The goal is to demonstrate security judgment, not just tool usage

## Intentional Misconfigurations

This project may include safe, controlled misconfigurations to generate realistic Prowler findings.

The purpose of these misconfigurations is to practice audit analysis, remediation planning, risk acceptance, and retesting.

Allowed intentional misconfigurations may include:

- An S3 bucket with weak or incomplete security settings
- An S3 bucket without versioning enabled
- An S3 bucket without default encryption enabled, where safe
- A security group allowing SSH from `0.0.0.0/0`, not attached to any running EC2 instance
- An IAM user without MFA
- A weak IAM password policy
- CloudTrail or logging gaps
- A test IAM access key created for audit purposes and later deleted or rotated

All intentional misconfigurations will be clearly documented and will not contain real data or expose running workloads.

## Out-of-Scope Items

The following items are out of scope for this project:

- Penetration testing
- Exploiting vulnerabilities
- Attacking AWS services
- Scanning third-party environments
- Uploading or processing sensitive data
- Creating production workloads
- Running public-facing applications
- Creating paid infrastructure
- Leaving insecure configurations active long term

This project is a defensive cloud security audit and remediation exercise.

## Audit Process

### 1. Prepare

The preparation phase defines the audit scope, safety controls, and environment setup.

Preparation activities include:

- Confirming the AWS account is safe to use
- Enabling root account MFA
- Configuring a budget alert
- Confirming the audit is performed from an IAM user, not the root account
- Defining which services are in scope
- Creating safe intentional misconfigurations
- Preparing the project documentation structure

### 2. Scan

Prowler will be used to scan the AWS account for security findings.

The scan will collect evidence across IAM, logging, networking, S3, encryption, and other AWS security controls.

The scan output will be saved in the `reports/` folder for later analysis.

Expected outputs may include:

- JSON report
- HTML report
- CSV report, if needed
- Terminal output summary

### 3. Analyze

The analysis phase focuses on interpreting the results instead of treating every finding equally.

Findings will be reviewed using the following questions:

- Is the affected resource actually in use?
- Is the resource exposed publicly?
- Does the issue involve sensitive data?
- Can the finding be exploited easily?
- What is the potential business or security impact?
- Is there a compensating control?
- Should the finding be remediated, accepted, or tracked for later?

Findings will be categorized as:

- Critical
- High
- Medium
- Low or informational
- Accepted risk

### 4. Report

The reporting phase will convert technical scan results into clear security documentation.

Two main reports will be created:

- `reports/executive-summary.md`
- `reports/detailed-findings.md`

The executive summary will be written for non-technical readers. It will explain the overall security posture, key risks, and remediation priorities.

The detailed findings report will be written for technical readers. It will include affected services, finding details, risk explanation, evidence, remediation steps, and retest status.

### 5. Remediate

Selected findings will be remediated based on risk priority.

Example remediation actions may include:

- Enabling MFA
- Strengthening the IAM password policy
- Deleting or rotating test access keys
- Restricting open security group rules
- Enabling S3 encryption
- Enabling S3 versioning
- Improving CloudTrail or logging configuration

Not every finding will be remediated immediately. Some findings may be accepted if they are low risk, not applicable, or have a valid compensating control.

### 6. Retest

After remediation, Prowler will be run again to confirm whether selected findings have been resolved.

The retest will help show measurable improvement in the AWS account’s security posture.

Before-and-after results will be documented to demonstrate the full audit lifecycle.

## Risk Prioritization Approach

Findings will be prioritized based on both severity and context.

The following factors will be considered:

- Exposure: Is the resource public or private?
- Exploitability: How easy is it to abuse the misconfiguration?
- Impact: What could happen if the issue is exploited?
- Data sensitivity: Does the resource contain sensitive data?
- Usage: Is the resource active, unused, or only created for testing?
- Blast radius: Could the issue affect one resource or the whole account?
- Remediation effort: Can the issue be fixed quickly and safely?

This approach helps separate real security risk from low-value scanner noise.

## Accepted Risk Approach

Some findings may be documented as accepted risks instead of being immediately remediated.

A finding may be accepted when:

- The finding does not apply to the environment
- The affected resource is unused
- The risk is very low in the current context
- A compensating control exists
- The cost or complexity of remediation is not justified for a test environment

Accepted risks will be documented in:

```text
remediation/accepted-risks.md
```

Each accepted risk will include:

- Finding name
- Severity
- Reason for acceptance
- Compensating controls, if any
- Review date
- Final decision

## Evidence Plan

Evidence will be collected throughout the project to support the GitHub portfolio, Medium blog, LinkedIn announcement, and video walkthrough.

Screenshots will only be taken when they provide useful audit evidence.

Planned screenshots include:

| Screenshot | Purpose |
|---|---|
| `01-root-mfa-enabled.png` | Shows root account MFA is enabled |
| `02-budget-alert-configured.png` | Shows cost control is in place |
| `03-prowler-scan-running.png` | Shows the audit scan being executed |
| `04-prowler-summary-before.png` | Shows initial scan results before remediation |
| `05-example-finding-before.png` | Shows one meaningful finding before remediation |
| `06-remediation-action.png` | Shows the remediation step in AWS |
| `07-prowler-summary-after.png` | Shows scan results after remediation |
| `08-before-after-comparison.png` | Shows improvement after remediation |

Screenshots will not include sensitive information such as:

- AWS account ID
- Access keys
- Secret keys
- Email addresses
- Full usernames
- Billing details

Sensitive information will be blurred or excluded before screenshots are added to the repository.

## Documentation Plan

The project documentation will be divided across the existing repository files.

| File | Purpose |
|---|---|
| `docs/methodology.md` | Explains how the audit was conducted |
| `docs/compliance-mapping.md` | Maps findings to security frameworks or benchmarks |
| `reports/executive-summary.md` | Summarizes risks for non-technical readers |
| `reports/detailed-findings.md` | Provides technical finding analysis |
| `remediation/critical-findings.md` | Documents urgent remediation items |
| `remediation/high-findings.md` | Documents high-priority remediation items |
| `remediation/medium-findings.md` | Documents medium-priority remediation items |
| `remediation/accepted-risks.md` | Documents risks that are accepted with justification |
| `scripts/run-prowler.sh` | Stores the command used to run Prowler |
| `scripts/parse-results.py` | Helps parse or summarize scan results |

No additional files will be created unless they are clearly needed.

## Limitations

This audit is limited by the size and design of the test AWS environment.

Because this is a personal portfolio project, it does not fully represent a large enterprise AWS environment with multiple AWS accounts, production workloads, centralized logging, organizational units, business applications, and dedicated security tooling.

The audit results are also influenced by which services are enabled in the account. Some Prowler findings may not apply because certain AWS services are not being used.

Despite these limitations, this project demonstrates the core professional workflow used in real cloud security audits:

- Define scope
- Collect evidence
- Run security tooling
- Interpret findings
- Prioritize risk
- Document accepted risk
- Remediate issues
- Retest and report improvement

## Success Criteria

This project will be considered successful when:

- The AWS account is prepared safely
- Prowler is run successfully
- Raw scan results are saved
- Findings are analyzed and prioritized
- Accepted risks are documented
- Selected findings are remediated
- A retest confirms improvement
- Final documentation is clear enough for GitHub, Medium, LinkedIn, and a video walkthrough

## Final Outcome

The final outcome of this project is a professional cloud security audit portfolio piece that shows more than tool usage.

It demonstrates the ability to:

- Run a cloud security audit
- Interpret scanner output
- Separate signal from noise
- Explain risk clearly
- Prioritize remediation
- Document accepted risks
- Communicate findings to both technical and non-technical audiences
- Show before-and-after security improvement
