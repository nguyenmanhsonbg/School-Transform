# Security Conventions

Status: DRAFT

## Purpose

Define minimum security expectations shared by every phase, module and channel.

## Security principles

- Tenant isolation is mandatory.
- Authorization is enforced through the shared RBAC capability.
- Sensitive actions are auditable.
- Security controls must be applied at API, business capability and infrastructure boundaries where appropriate.
- Security requirements must not be weakened for a particular application channel.

## Baseline controls

- Encrypt data in transit.
- Hash passwords using an appropriate one-way password hashing mechanism.
- Protect and manage sessions.
- Mask or restrict sensitive data in responses, logs and exports.
- Apply rate limiting where abuse or resource exhaustion is plausible.
- Validate uploaded files and control public versus private access.
- Record access and security-relevant events.
- Maintain database backup, retention and restore testing.
- Monitor application and integration failures.

## Access control

Authentication establishes identity. RBAC evaluates role and scope. Multi-tenancy establishes the data boundary. All three concerns must be preserved for web, mobile, import, export, report, background and integration flows.

## Audit event minimum

For significant actions, an audit event must retain, at minimum:

- Actor.
- Time.
- Function or capability.
- Affected data object.
- Value before the action, when applicable.
- Value after the action, when applicable.
- Tenant.
- Device or IP information when required.

The owning capability determines which actions are significant, while this field minimum remains a shared cross-cutting rule.

## Sensitive actions

At minimum, the following require explicit authorization and audit:

- Login and logout events where operationally relevant.
- Account activation, lock and permission changes.
- Student-data changes.
- Grade changes and unlock operations.
- Imports and exports.
- Access to sensitive files or reports.
- Cross-tenant administration if it is introduced.

## Secure data handling

Credentials and secrets must not be logged. Error responses must not disclose sensitive data or internal implementation details. File and integration credentials require controlled storage and rotation policies when those capabilities are designed.

## Open Questions

- Which data categories require field-level masking or encryption?
- Is multi-factor authentication required for specific roles?
- What rate limits, backup retention and restore objectives apply to the pilot?
- Which security events require alerting in addition to audit logging?
- What compliance and data residency requirements apply?
