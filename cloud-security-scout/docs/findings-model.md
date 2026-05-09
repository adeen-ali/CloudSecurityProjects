# Findings Model

Each security issue detected by Cloud Security Scout will be stored as a finding.

## Finding Fields

| Field | Purpose |
|---|---|
| finding_id | Unique ID for the finding |
| service | AWS service where the issue was found |
| resource_id | Affected AWS resource |
| severity | Risk level such as HIGH, MEDIUM, or LOW |
| finding_type | Type of security issue |
| description | Explanation of the issue |
| recommendation | Suggested remediation |
| status | Current state of the finding |
| timestamp | Time when the finding was detected |

## Example Finding

```json
{
  "finding_id": "sg-12345-ssh-open",
  "service": "EC2",
  "resource_id": "sg-12345",
  "severity": "HIGH",
  "finding_type": "SSH_OPEN_TO_WORLD",
  "description": "Security group allows SSH access from 0.0.0.0/0.",
  "recommendation": "Restrict SSH access to a trusted IP range.",
  "status": "OPEN",
  "timestamp": "2026-05-09T10:00:00Z"
}
```

## Why This Model Is Needed

A consistent findings model makes the scanner easier to extend.

Every new check can store results in the same format, whether the issue comes from EC2, S3, IAM, EBS, RDS, or AI-related cloud resources.
