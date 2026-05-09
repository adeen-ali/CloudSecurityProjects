# Cloud Security Scout

Cloud Security Scout is a serverless AWS security scanner designed to detect risky cloud configurations, store findings, and send alerts for high-risk issues.

The project focuses on practical cloud security automation using AWS Lambda, Python Boto3, DynamoDB, SNS, EventBridge, and CloudWatch.

## Purpose

Modern cloud environments can grow quickly, making it difficult to manually track insecure configurations. This project automates basic security checks and helps identify risks such as exposed management ports and unauthorized GPU instances that may indicate shadow AI or cost-drain activity.

## Planned Features

- Detect security groups exposing SSH to the internet
- Detect security groups exposing RDP to the internet
- Detect running GPU instances used for high-cost workloads
- Store findings in DynamoDB
- Send SNS alerts for high-severity findings
- Run automatically using EventBridge
- Log scanner activity in CloudWatch

## Architecture

EventBridge triggers a Lambda function on a schedule. The Lambda function uses Boto3 to scan AWS resources, stores findings in DynamoDB, and sends alerts through SNS for high-risk findings.

## Project Status

Work in progress.
