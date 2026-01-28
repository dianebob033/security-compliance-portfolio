# Evidence Requirements (Audit-Ready)

## Evidence Principles
- Evidence must be: repeatable, timestamped, access-controlled, and attributable.

## Evidence Sources (Examples)
- IAM: users/roles/policies exports, access review records
- Logging: CloudTrail settings, CloudWatch alarms, retention configs
- Encryption: KMS key policies, S3 encryption settings
- Backups: backup job logs, restore test results
- Change Mgmt: change tickets, approvals, deployment logs

## Evidence Collection Cadence
- Continuous: (CloudTrail enabled, encryption settings)
- Monthly: (backup job status summary)
- Quarterly: (access review)
- Annually: (tabletop exercise)
