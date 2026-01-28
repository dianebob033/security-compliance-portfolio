# Logging & Monitoring Standard

## Objective
Ensure sufficient logging, retention, and alerting to support detection and auditability.

## Required Logs
- CloudTrail management events
- Authentication events
- Admin/IAM changes
- S3 access logs (if applicable)
- Application logs (basic)

## Retention
- Hot retention: X days
- Archive: X months/years
- Rationale: (audit/forensics)

## Alerting (High-Risk Events)
- Root account activity
- IAM policy changes
- Multiple failed logins
- CloudTrail disabled attempt
- KMS key policy changes

## Access to Logs
- Restricted to Security/Cloud admins
- Read-only where possible
- Integrity controls (S3 policy, encryption)

## Evidence
- CloudTrail config, alarm rules, retention settings
