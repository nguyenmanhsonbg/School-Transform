# Authentication

Status: DRAFT

## Purpose

Define the authentication behavior that establishes a trusted user identity before RBAC and tenant authorization are evaluated.

## Scope

This document refines the [Identity Specification](specification.md) and follows [Security Conventions](../../90-cross-cutting/security.md). It does not select a credential provider, token format or SSO vendor.

## Confirmed capabilities

- Sign in.
- Sign out.
- Change password.
- Password recovery and reset.
- Account activation.
- Account locking.
- Session management.
- Preparation for future SSO.

## Proposed authentication flow

1. A user presents an approved credential or identity-provider assertion.
2. The platform verifies the credential or assertion.
3. The platform resolves the account and its permitted tenant contexts.
4. The platform creates an authenticated session.
5. Each protected request carries the authenticated actor context to RBAC and tenant isolation.
6. Sign out, expiration, lock or deactivation invalidates the applicable session according to the final session policy.

The flow is proposed at the behavior level. The implementation mechanism remains open.

## Password and recovery behavior

- Passwords must be stored only as one-way password hashes.
- Passwords and recovery secrets must not appear in logs or audit payloads.
- Recovery must not disclose whether an unrelated account exists.
- Reset and activation operations must expire according to the final security policy.
- Password changes and resets must be auditable as security-relevant actions.

## Session behavior

Sessions should have an explicit lifecycle, expiration policy and revocation behavior. Account lock or deactivation must prevent new authenticated activity and define what happens to active sessions.

## SSO preparation

The platform should keep an integration boundary for future SSO without making SSO a Phase 0 requirement. The identity subject, tenant context and role mapping from an external provider must still be evaluated by platform policy.

## Open Questions

- Credentials only, SSO, or a staged combination for the first pilot?
- Is MFA mandatory for administrators or other sensitive roles?
- Which session mechanism, expiration and revocation policy is required?
- How are external identities mapped to a person, account, tenant and role?
- Which identity protocols and providers must be supported?
