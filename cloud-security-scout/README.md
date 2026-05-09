# Cloud Security Scout

Cloud Security Scout is a serverless AWS security scanner that detects risky cloud configurations, stores findings, and sends alerts for high-risk issues.

This project focuses on practical cloud security automation using AWS Lambda, Python Boto3, DynamoDB, SNS, EventBridge, and CloudWatch. It also includes an AI-security-aware extension for detecting possible shadow AI or cost-drain activity, such as unauthorized GPU-based workloads.

## Why This Project Exists

Modern cloud environments can grow quickly. Manually checking every resource for insecure configurations is slow, inconsistent, and easy to miss.

Cloud Security Scout automates these checks so risky configurations can be detected, recorded, and reported.

## Planned Architecture

EventBridge → Lambda → AWS Resource Checks → DynamoDB → SNS Alerts → Dashboard

## What It Will Detect

- Security groups exposing SSH to the internet
- Security groups exposing RDP to the internet
- Public S3 bucket risks
- Unencrypted EBS volumes
- IAM users without MFA
- Running GPU instances that may indicate shadow AI or cost-drain activity

## Why These Services Are Used

### EventBridge

EventBridge triggers the scanner on a schedule. Lambda does not run by itself continuously, so EventBridge acts like the scheduler that tells Lambda when to run.

### Lambda

Lambda runs the Python scanner code without needing a server. This is suitable because the scanner only needs to run for a short time, check resources, save findings, send alerts, and stop.

### Boto3

Boto3 allows the Python code to communicate with AWS services and inspect resources such as security groups, EC2 instances, S3 buckets, and IAM users.

### DynamoDB

DynamoDB stores the security findings so results are not lost after Lambda finishes running. This also allows findings to be reviewed over time.

### SNS

SNS sends alerts when high-risk findings are detected.

### CloudWatch

CloudWatch stores logs from Lambda so scanner activity and errors can be reviewed.

### Dashboard

The dashboard will provide a simple visual view of findings, severity levels, affected resources, and remediation guidance.

## Status

Work in progress.
