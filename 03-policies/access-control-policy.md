# Access Control Policy

## Purpose
Define access control requirements to protect systems and data.

## Scope
Applies to all users, contractors, and systems within the AWS environment.

## Policy Statements
1. MFA required for privileged roles.
2. Least privilege: access granted by role, not by individual exceptions.
3. No shared accounts. No long-lived access keys unless approved.
4. Access reviews conducted quarterly.
5. Termination/offboarding access removed within X hours.

## Roles & Responsibilities
- Security: policy owner, review cadence
- Engineering: implement controls
- Managers: approve access

## Exceptions
- Must be documented with justification, time-bound, and approved.

## Evidence / Records
- Access requests, approvals, review logs, IAM exports

## Review Cadence
- Quarterly (or semi-annually)
