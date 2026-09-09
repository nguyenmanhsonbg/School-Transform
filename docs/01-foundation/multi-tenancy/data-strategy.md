# Tenant Data Strategy

Status: DRAFT

## Purpose

Define data classification and ownership rules needed to make tenant isolation, configuration and future scaling consistent.

## Scope

This is a conceptual data strategy based on the [Multi-tenancy Specification](specification.md) and [Database Conventions](../../90-cross-cutting/database-conventions.md). It does not select a database engine, hosting vendor or final schema.

## Data classifications

| Classification | Meaning | Initial direction |
|---|---|---|
| Platform-global | Shared metadata that is not owned by a school | Keep minimal and explicitly identified |
| Tenant-owned | Business records belonging to one school | Must carry tenant association |
| Tenant configuration | Settings that change behavior for one school | Scoped to tenant and, where applicable, module or academic year |
| External reference | Data owned by another system | Keep ownership and synchronization direction explicit |
| Operational record | Logs, integration records, audit and delivery state | Preserve originating tenant when the event is tenant-scoped |

## Tenant key rule

The tenant association of a business record must be unambiguous. A missing tenant association must not be interpreted as global data. The exact physical representation remains a technical decision.

## Configuration scopes

The source roadmap identifies these possible configuration levels:

- Tenant.
- Module.
- Academic Year.

Configuration should support defaults, versioning and effective periods where required. The configuration capability owns the behavior of configuration values; business modules own the meaning of their domain values.

## History and lifecycle

The domain explicitly requires student class history and student status history. Other modules must state whether a change is mutable, historized, archived or immutable rather than assuming one deletion policy for all data.

## Import and export

Data exchange must follow:

Upload → Validate → Preview → Show Error → Confirm → Import → Audit

Exports must also preserve tenant boundaries and access permissions. Large imports and reports may require background processing, while their operational state remains traceable to the initiating tenant and actor.

## Backup and recovery direction

Backup, retention, restore testing and backup audit are platform concerns. Recovery procedures must preserve tenant isolation and must not restore one tenant's data into another tenant context.

## Candidate physical strategies

The following are options for later evaluation:

- Shared database with tenant-aware records.
- Separate schema per tenant.
- Separate database per tenant.
- Hybrid strategy based on tenant size or compliance.

No option is selected by this document.

## Open Questions

- Which physical strategy fits the first pilot's scale, cost and isolation needs?
- Which uniqueness constraints are platform-wide versus tenant-scoped?
- Which data requires archival or immutable history?
- What are the retention, export, deletion and restore guarantees?
- Will reporting later require a separate read model?
