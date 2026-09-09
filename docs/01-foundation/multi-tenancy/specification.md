# Multi-tenancy Specification

Status: DRAFT

## Purpose

Define the business meaning of a tenant and the minimum tenant-aware behavior required by the platform.

## Scope

This specification covers tenant identity, lifecycle, data isolation and tenant-scoped configuration at a business level. Physical database isolation and deployment choices are intentionally deferred.

## Baseline model

Each school is treated as one tenant in the initial product model. One platform may serve multiple school tenants.

Every core business record must be attributable to a tenant. Tenant-specific configuration may differ without changing the shared product code.

## Tenant capabilities

- Create a tenant.
- Update school information.
- Activate or deactivate a tenant.
- Configure tenant name, code, logo, timezone, language and enabled modules.
- Maintain tenant-specific settings.
- Prepare for a future model in which one customer may manage more than one school.

## Isolation rules

- A request that accesses tenant business data must have an explicit tenant context.
- A user operating within tenant A must not read or modify tenant B data by default.
- Tenant context must be enforced consistently for reads, writes, imports, exports, files, notifications, reports and audit records.
- Cross-tenant administration, if required, must be an explicit platform-level capability with separate authorization and audit.
- Tenant configuration must not leak into another tenant's behavior.

## Tenant-aware foundation

Identity establishes which user is acting. RBAC establishes whether the action is allowed. This specification establishes where the action is allowed. Audit records must retain the tenant context for significant actions.

## Out of scope

- Database-per-tenant versus shared-database strategy.
- Tenant billing and subscription management.
- Cross-tenant analytics.
- Tenant migration or data export procedures.

## Open Questions

- Is School always one-to-one with Tenant, or will a tenant be able to contain multiple schools?
- What physical isolation strategy will be selected?
- Which platform administrators can perform cross-tenant actions?
- What are the tenant retention, archival and deletion rules?
- Must tenant code be globally unique across the platform?

