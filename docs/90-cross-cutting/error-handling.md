# Error Handling Conventions

Status: DRAFT

## Purpose

Define a consistent way to classify, expose, log and audit failures across APIs, modules, background work and integrations.

## Scope

This document complements [API Conventions](api-conventions.md) and [Security Conventions](security.md). It does not define framework-specific exception types or a module's business error catalog.

## Error categories

| Category | Meaning | External behavior |
|---|---|---|
| Validation | Input cannot satisfy the declared contract | Return actionable field or object details |
| Authentication | The actor cannot be authenticated | Do not disclose sensitive account details |
| Authorization | The actor lacks permission or scope | Deny without revealing protected data |
| Not found | The requested resource is unavailable in the permitted context | Avoid leaking another tenant's existence |
| Conflict | The request conflicts with current state or uniqueness rules | Explain the business conflict safely |
| Business rule | The request is understood but not allowed by domain policy | Return a stable business error code |
| Dependency | An external or shared dependency failed | Return a safe operational response and record context |
| Unexpected | An unclassified failure occurred | Return a generic error and preserve diagnostic details internally |

## API error shape

The shared API response should provide:

- Stable machine-readable error code.
- Safe human-readable message.
- Field, object or rule details when useful.
- Correlation ID.
- Retry guidance when the operation can be retried safely.

The final response schema is an open decision.

## Handling rules

- Validate at the interface boundary and enforce business rules in the owning capability.
- Do not expose stack traces, credentials, internal queries or cross-tenant details.
- Log unexpected and dependency failures with correlation and tenant context when applicable.
- Do not log the same error repeatedly at every layer without adding context.
- A caller either handles an error or returns it with context; it must not silently discard it.
- Retried operations must define idempotency and duplicate-effect behavior.

## Background and integration failures

Long-running imports, reports, notifications and integrations should expose an observable operation state. A failure must retain enough context for support and reconciliation without exposing secrets or unrelated tenant data.

## Open Questions

- What exact error envelope and code taxonomy will be standardized?
- Which failures are retryable and how are retry limits defined?
- How are validation messages localized?
- How are partial import and batch failures reported?
- Which operational errors require alerting in addition to logging?
