# AWS Security Controls Checklist (Baseline)

> Purpose: A practical, audit-ready baseline controls set for a small-to-medium AWS environment.
> Style: Each control includes requirement, implementation notes, evidence, owner, and review frequency.

---

## 1) IAM & Access Control

### IAM-01: MFA for Privileged Access
- Requirement: Enforce MFA for all users with administrative or privileged permissions.
- Implementation Notes: Use IAM Identity Center (preferred) or IAM user MFA; restrict console access without MFA.
- Evidence: Screenshot/export of MFA status for privileged identities; IAM/SSO settings.
- Owner: Security / IT
- Frequency: Continuous + Quarterly review

### IAM-02: Least Privilege Role Design
- Requirement: Grant access via roles and least privilege policies; avoid broad `*:*` permissions.
- Implementation Notes: Prefer job-function roles; separate admin, deploy, read-only roles.
- Evidence: Role/policy documents; policy review notes; access approvals.
- Owner: Security + Engineering
- Frequency: Quarterly

### IAM-03: Access Review Process
- Requirement: Perform periodic access reviews for users/roles/groups and remove unnecessary access.
- Implementation Notes: Review privileged access first; document decisions and approvals.
- Evidence: Access review record (date, reviewer, findings, actions).
- Owner: Security
- Frequency: Quarterly

### IAM-04: Root Account Protection
- Requirement: Root account is locked down with MFA; no day-to-day usage.
- Implementation Notes: Store root credentials securely; enable alerts for root usage.
- Evidence: MFA enabled proof + CloudTrail/root-usage alert rule.
- Owner: Security
- Frequency: Continuous

---

## 2) Logging & Monitoring

### LOG-01: CloudTrail Enabled (All Regions)
- Requirement: CloudTrail enabled for management events across all regions.
- Implementation Notes: Enable organization trail if multi-account; store logs in dedicated S3 bucket.
- Evidence: CloudTrail configuration screenshot/export; log delivery verification.
- Owner: Cloud/SRE + Security
- Frequency: Continuous

### LOG-02: Centralized Log Storage with Retention
- Requirement: Logs stored centrally with defined retention and restricted access.
- Implementation Notes: S3 bucket encryption; retention policy; least-privilege access to logs.
- Evidence: S3 bucket policy; encryption settings; retention configuration.
- Owner: Cloud/SRE
- Frequency: Quarterly

### LOG-03: Alerts for High-Risk Events
- Requirement: Alerts for IAM changes, root activity, CloudTrail tampering, suspicious auth activity.
- Implementation Notes: Use CloudWatch/EventBridge + SNS; define severity routing.
- Evidence: Alarm/rule list; alert routing configuration.
- Owner: Security
- Frequency: Monthly check + Quarterly review

---

## 3) Data Protection & Encryption

### ENC-01: Encryption at Rest for Sensitive Data
- Requirement: Encrypt sensitive data at rest (S3, RDS, EBS) using KMS where applicable.
- Implementation Notes: Default encryption; key rotation; restrict KMS key admin usage.
- Evidence: KMS key settings; S3/RDS encryption configuration.
- Owner: Cloud/SRE
- Frequency: Quarterly

### ENC-02: Encryption in Transit
- Requirement: Enforce TLS for external endpoints and internal service communication where feasible.
- Implementation Notes: Use HTTPS/ALB TLS policies; document exceptions.
- Evidence: TLS configuration evidence; endpoint test notes.
- Owner: Engineering + Security
- Frequency: Quarterly

---

## 4) Backup & Recovery

### BAK-01: Backup Policy and Schedule
- Requirement: Define backup frequency and retention for critical systems/data.
- Implementation Notes: Automate backups; store in separate location/account when possible.
- Evidence: Backup job configuration; backup reports.
- Owner: Cloud/SRE
- Frequency: Monthly

### BAK-02: Restore Testing
- Requirement: Periodically test restores to validate recoverability.
- Implementation Notes: Tabletop + at least one technical restore test.
- Evidence: Restore test record (date, scope, result, issues).
- Owner: Cloud/SRE + Security
- Frequency: Quarterly / Semi-annually

---

## 5) Change Management (Lightweight)

### CHG-01: Change Approval & Tracking
- Requirement: Track changes for security-relevant configurations (IAM, logging, networking).
- Implementation Notes: Use ticketing (GitHub Issues acceptable); require approval for high-risk changes.
- Evidence: Change tickets/PRs; approvals; deployment logs.
- Owner: Engineering + Security
- Frequency: Ongoing

---

## 6) Vendor / Third-Party (Baseline)

### VEN-01: Vendor Security Review (Lite)
- Requirement: Assess vendors that handle sensitive data or production access.
- Implementation Notes: Use a checklist; require incident notification SLA.
- Evidence: Completed vendor checklist; decision record.
- Owner: Security + Business owner
- Frequency: Before onboarding + Annual review

---

## 7) Incident Readiness (Baseline)

### IR-01: Incident Response Playbook (Lite)
- Requirement: Document roles, severity levels, and response steps.
- Implementation Notes: Define who leads, who communicates, and evidence preservation steps.
- Evidence: Playbook doc; tabletop notes.
- Owner: Security
- Frequency: Annual review
