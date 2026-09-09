# Integration Principles

Status: DRAFT

## Purpose

Define how the platform prepares for and governs connections to external systems without coupling core business rules to a provider.

## Scope

This document covers Phase 0 integration preparation and the principles for the later Integration Hub. It follows [API Conventions](api-conventions.md), [Security Conventions](security.md) and [Multi-tenancy](../01-foundation/multi-tenancy/specification.md). It does not define a provider-specific contract.

## Supported patterns

The roadmap identifies these exchange patterns:

- REST API.
- Webhook.
- API key.
- Excel.
- CSV.
- SFTP.
- Message queue.
- SSO.

The first phase needs a clear framework boundary and import/export behavior; not every pattern is required for the MVP.

## Integration boundaries

- The owning business module retains the meaning of its data.
- An integration adapter translates external representations into the owning module contract.
- External credentials and secrets are managed outside business records and are never logged.
- Mapping, retry, integration state and error details belong to integration concerns.
- External callbacks must be authenticated, tenant-aware and idempotent where duplicate delivery is possible.
- An external system must not bypass tenant isolation, RBAC, audit or validation.

## Operational capabilities

The later Integration Hub is expected to provide:

- API credentials.
- Integration mapping.
- Retry.
- Integration log.
- Error log.
- Webhook management.

These capabilities must be designed so that a failure can be reconciled without silently mutating business state.

## Import and export

Core imports and exports use the shared flow:

Upload → Validate → Preview → Show Error → Confirm → Import → Audit

Large exchanges may run asynchronously, but the initiating actor, tenant, source, outcome and errors must remain observable.

## Open Questions

- Which external systems are required for the first pilot?
- Which integration patterns are required in Phase 0 versus Phase 3?
- What authentication and signature rules apply to webhooks?
- How are mapping versions and schema changes managed?
- What retry, reconciliation and dead-letter behavior is required?
