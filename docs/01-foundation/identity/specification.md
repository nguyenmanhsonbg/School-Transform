# Identity Specification

Status: DRAFT

## Purpose

Define the identity and account capability required to authenticate users and establish a trusted actor context for the platform.

## Scope

This specification covers account lifecycle, authentication entry points and session context at a baseline level. Authorization rules belong to RBAC.

## Actors and identity subjects

The platform must support accounts for at least:

- System Administrator.
- School Administrator.
- Ban Giám hiệu and other staff.
- Teachers.
- Students.
- Parents or guardians.

The relationship between a person, a school role and a login account must remain explicit. A parent may be linked to multiple students, and a student may have multiple guardians.

## Baseline capabilities

- Sign in.
- Sign out.
- Change password.
- Request password recovery.
- Reset password.
- Activate an account.
- Lock or deactivate an account.
- Manage active sessions.
- Prepare for future SSO integration.

## Authentication context

After successful authentication, the platform establishes the user identity and the tenant context needed for subsequent authorization. Identity does not decide which school data or module actions the user may access.

## Lifecycle expectations

Account status changes must be auditable when they affect access. Deactivation or lock must prevent new authenticated activity according to the final session policy.

## Security boundary

Credentials, sessions and recovery flows must follow the security conventions. Passwords must never be stored or logged in recoverable form. Detailed authentication mechanisms require an ADR when selected.

## Open Questions

- Which credential and session mechanism will be used?
- Is multi-factor authentication required for administrators?
- How are accounts invited, verified and linked to an existing teacher, student or parent?
- Can one account belong to multiple tenant contexts?
- Which SSO providers and protocols are required?
- What happens to active sessions after lock, deactivation or tenant removal?

