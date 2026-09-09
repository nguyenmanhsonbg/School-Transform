# ADR-002: School as Initial Tenant Boundary

Status: Proposed

## Purpose

Record the initial tenant boundary and the isolation requirement that must be preserved across the platform.

## Context

The platform is intended to serve multiple THPT schools. Tenant-specific configuration and data isolation are required from the foundation, while the source roadmap does not yet define the physical persistence topology.

## Decision

Treat each school as one tenant in the initial product model.

All tenant-owned business data, configuration, files, notifications, reports and audit records must preserve tenant association. A user operating within one tenant must not access another tenant by default. Cross-tenant administration, if required, is a separate platform capability with explicit authorization and audit.

## Affected documentation

- [Multi-tenancy Specification](../01-foundation/multi-tenancy/specification.md)
- [Database Conventions](../90-cross-cutting/database-conventions.md)
- [API Conventions](../90-cross-cutting/api-conventions.md)
- [Security Conventions](../90-cross-cutting/security.md)

## Alternatives considered

- Build a separate product deployment for every school.
- Use a single global school context without tenant isolation.
- Introduce a multi-school hierarchy inside one tenant from the first release.

## Rationale

- It supports the product goal of one reusable platform for multiple schools.
- It makes isolation and tenant-specific configuration first-class foundation concerns.
- It does not force a physical database strategy before operational requirements are known.

## Consequences

### Positive

- Tenant isolation is visible in domain, API, security and data conventions.
- Configuration can vary by school without forking the core product.
- The platform can grow toward a multi-school operating model.

### Trade-offs

- Every request, background task, import, export, report and integration must preserve tenant context.
- Incorrect tenant filtering becomes a high-severity security risk.
- The final persistence and backup strategy must account for tenant isolation and recovery.

## Deferred decisions

The following are intentionally not decided by this ADR:

- Shared database versus database-per-tenant.
- Tenant hierarchy and multi-school customer accounts.
- Billing, subscription and commercial tenancy.
- Cross-tenant analytics and administration policies.

## Open Questions

- Is the business relationship always one School to one Tenant?
- Which platform roles can perform cross-tenant actions?
- What retention, export, archival and deletion guarantees are required?
