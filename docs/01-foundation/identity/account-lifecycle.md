# Account Lifecycle

Status: DRAFT

## Purpose

Define the account lifecycle and access transitions needed to manage platform users safely.

## Scope

This document describes account state behavior for the [Identity Specification](specification.md) and [Authentication](authentication.md). It does not define the complete person model or detailed authentication protocol.

## Proposed states

| State | Meaning |
|---|---|
| Pending activation | An account exists but has not completed activation; proposed for confirmation |
| Active | The account may authenticate; tenant isolation and RBAC determine protected access after authentication |
| Locked | Authentication is blocked by security or administrative action |
| Deactivated | The account is intentionally disabled and cannot start new authenticated activity |

The final state names and whether Pending activation is required remain open.

## Lifecycle operations

- Create an account or establish an external identity link.
- Activate an account.
- Update account contact and recovery information.
- Change credentials.
- Lock an account.
- Unlock an account with appropriate authorization.
- Deactivate an account.
- Restore an account only through an explicitly authorized operation.
- Review and revoke active sessions.

## Relationship to school roles

An account is not itself a permission. A user may receive one or more roles within one or more tenant contexts, subject to the final multi-tenant and RBAC rules. Linking a teacher, student or parent record to an account must be explicit and auditable.

## State transition guardrails

- Lock, unlock, activation and deactivation require explicit authorization.
- Access-affecting transitions are audited.
- Deactivation must not delete business history owned by the person or account relationship.
- A locked or deactivated account cannot bypass identity controls through another channel.
- Reuse of an identifier after deactivation must follow the final uniqueness and retention policy.

## Bulk and import operations

Teacher, student and parent imports may create or update account relationships. Imports must use the shared validation, preview, confirmation and audit flow and must not activate accounts implicitly unless the import policy explicitly allows it.

## Open Questions

- Is account creation invitation-based, administrator-created, self-service or role-specific?
- Which account fields are globally unique versus tenant-scoped?
- What is the exact behavior for active sessions after each state transition?
- Can a user retain an account while all tenant roles are removed?
- How are duplicate people or duplicate external identities resolved?
