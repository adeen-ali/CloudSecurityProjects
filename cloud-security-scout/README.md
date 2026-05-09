# Cloud Security Scout

Cloud Security Scout is a serverless AWS security scanner designed to detect risky cloud configurations, store findings, and send alerts for high-risk issues.

The project focuses on practical cloud security automation and includes an AI-security-aware extension for detecting possible shadow AI or cost-drain activity, such as unauthorized GPU-based workloads.

## What It Detects

- Security groups exposing SSH to the internet
- Security groups exposing RDP to the internet
- Public S3 bucket risks
- Unencrypted cloud resources
- IAM users without MFA
- Running GPU instances that may indicate unauthorized AI/ML workloads

## Why This Matters

Modern cloud environments grow quickly, and manually checking every resource is not realistic. Misconfigured resources can expose systems to attackers, create compliance gaps, or increase cloud costs.

As AI adoption increases, organizations also face new risks such as unapproved AI workloads, over-permissive access to AI services, and expensive GPU usage. This project adds a lightweight shadow AI detection layer while keeping the foundation focused on cloud security.
