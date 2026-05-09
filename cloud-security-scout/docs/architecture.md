# Architecture

Cloud Security Scout uses a serverless architecture to scan AWS resources for risky configurations.

## Flow

EventBridge → Lambda → AWS Resource Checks → DynamoDB → SNS Alerts → Dashboard

## Why EventBridge?

EventBridge triggers the scanner on a schedule.

Lambda does not run continuously by itself. It needs an event to start execution. EventBridge acts as the scheduler that invokes the Lambda function at fixed intervals, such as daily or every few hours.

## Why Lambda?

Lambda runs the Python scanner code without needing a server.

This is suitable because the scanner only needs to run for a short time, check resources, save findings, send alerts, and stop.

## Why Boto3?

Boto3 is the AWS SDK for Python.

The Lambda function uses Boto3 to inspect AWS resources such as EC2 security groups, EC2 instances, S3 buckets, IAM users, and other cloud resources.

## Why DynamoDB?

DynamoDB stores security findings.

Lambda executions are temporary, so findings need persistent storage. DynamoDB allows us to keep a history of findings over time.

## Why SNS?

SNS sends alerts when high-risk findings are detected.

If the scanner detects something serious, such as SSH open to the internet or a suspicious GPU instance, SNS can notify the security team by email.

## Why CloudWatch?

CloudWatch stores Lambda logs.

These logs help verify that the scanner ran successfully and help troubleshoot errors.

## Why a Dashboard?

The dashboard will provide a simple visual view of findings, severity levels, affected resources, and remediation guidance.
