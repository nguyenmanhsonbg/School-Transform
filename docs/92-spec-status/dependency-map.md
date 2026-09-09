# Dependency Map

Status: DRAFT

## Purpose

Show the dependency order between product direction, foundation capabilities and later business modules. The map guides sequencing but does not prohibit justified parallel work.

## Dependency principles

- Product direction and glossary precede domain interpretation.
- Domain model and boundaries precede module ownership.
- Architecture and tenant context precede technical conventions.
- Identity establishes the actor; RBAC establishes permission; tenant isolation establishes data boundary.
- Shared capabilities precede modules that consume them.
- Phase is a milestone, not a single dependency node.

## Governing documents

These documents govern direction, principles and architectural decisions. They are not all sequencing nodes, but changes to them require review of affected dependencies:

- [Product Principles](../00-product/product-principles.md)
- [Product Roadmap](../00-product/roadmap.md)
- [ADR-001 — Modular Monolith baseline](../91-decisions/ADR-001-modular-monolith.md)
- [ADR-002 — Multi-tenancy boundary](../91-decisions/ADR-002-multi-tenancy.md)

## Product and foundation dependency

| Order | Capability or document | Depends on | Enables |
|---:|---|---|---|
| 1 | [Product Vision](../00-product/product-vision.md) | Source context | Product scope |
| 2 | [Product Scope](../00-product/product-scope.md) | Product vision | Roadmap and domain |
| 3 | [Glossary](../00-product/glossary.md) | Product direction | Consistent terminology |
| 4 | [Domain Model](../01-foundation/domain/domain-model.md) | Scope and glossary | Domain boundaries |
| 5 | [Domain Boundaries](../01-foundation/domain/domain-boundaries.md) | Domain model and roadmap | Modular architecture |
| 6 | [System Context](../01-foundation/architecture/system-context.md) | Scope and domain overview | System architecture |
| 7 | [System Architecture](../01-foundation/architecture/system-architecture.md) | Context and domain model | Modular and deployment architecture |
| 8 | [Modular Architecture](../01-foundation/architecture/modular-architecture.md) | System architecture and boundaries | Module specifications |
| 9 | [Multi-tenancy](../01-foundation/multi-tenancy/specification.md) | Domain and architecture | Tenant isolation and data strategy |
| 10 | [Identity](../01-foundation/identity/specification.md) | Tenant baseline | Authentication and account lifecycle |
| 11 | [RBAC](../01-foundation/rbac/specification.md) | Identity and tenant baseline | Permission model |
| 12 | [API Conventions](../90-cross-cutting/api-conventions.md) | Architecture, identity and RBAC | Module APIs |
| 13 | [Database Conventions](../90-cross-cutting/database-conventions.md) | Domain and tenant strategy | Module data models |
| 14 | [Security Conventions](../90-cross-cutting/security.md) | Tenant, identity and RBAC | All protected flows |

## Foundation detail dependency

| Capability | Depends on | Used by |
|---|---|---|
| [Tenant isolation](../01-foundation/multi-tenancy/tenant-isolation.md) | [Multi-tenancy specification](../01-foundation/multi-tenancy/specification.md) | All tenant-owned operations |
| [Tenant data strategy](../01-foundation/multi-tenancy/data-strategy.md) | Multi-tenancy and [database conventions](../90-cross-cutting/database-conventions.md) | Module data models, backup and reporting |
| [Authentication](../01-foundation/identity/authentication.md) | [Identity specification](../01-foundation/identity/specification.md) and [security conventions](../90-cross-cutting/security.md) | Every protected channel |
| [Account lifecycle](../01-foundation/identity/account-lifecycle.md) | Identity and authentication | User and role administration |
| [Permission model](../01-foundation/rbac/permission-model.md) | [RBAC specification](../01-foundation/rbac/specification.md) and tenant isolation | Every module action |
| [Error handling](../90-cross-cutting/error-handling.md) | [API](../90-cross-cutting/api-conventions.md) and security conventions | APIs, jobs and integrations |
| [Logging and monitoring](../90-cross-cutting/logging-monitoring.md) | Error, API and security conventions | Operations and support |
| [Testing strategy](../90-cross-cutting/testing-strategy.md) | All shared conventions | Status gates and release verification |
| [Integration principles](../90-cross-cutting/integration-principles.md) | API, security and tenant conventions | Import/export and Integration Hub |
| [Deployment architecture](../01-foundation/architecture/deployment-architecture.md) | System architecture and cross-cutting conventions | DEV, UAT and PROD delivery |

## Phase 1 conceptual dependency

The current School Core path is:

School structure → Academic Year → Class → Student and Teacher → Subject → Teaching Assignment → Timetable → Attendance and Grading.

Parent, Notification, Audit, Import/Export and Reporting support this path. Their final module boundaries must be confirmed before the Phase 1 specifications are created.

## Later phase dependency

- Phase 2 Request / Workflow Platform precedes request types and approval-driven processes.
- Phase 3 shared Integration Hub precedes provider-specific integrations.
- Phase 4 AI Platform precedes assistants, analytics, risk detection and report generation.
- AI features require mature data, digitized workflows, clear permissions and audit.

## Parallel work

Audit, File Management, Notification and Configuration can be specified in parallel after tenant, identity, RBAC and cross-cutting baselines are sufficiently clear. Parallel work must still use the same glossary, security rules and dependency map.

## Open Questions

- Which Phase 1 naming decisions must be resolved before module folders are created?
- Which foundation capabilities are blocking the first coding milestone?
- Should Reporting have a shared dependency node or remain a consumer of source modules?
- Which dependencies require synchronous contracts, asynchronous operations or both?
