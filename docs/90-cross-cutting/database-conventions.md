# Database Conventions

Status: DRAFT

## Purpose

Define shared data-management principles for modules in the Modular Monolith without prematurely selecting a database product.

## Scope

This document covers conceptual persistence conventions, tenant safety, migrations, history and operational data concerns. Physical schema details belong in module data-model documents.

## Core conventions

- Every tenant-owned business record must have an unambiguous tenant association.
- Entity and field names follow the approved glossary and module ownership.
- Relationships and lifecycle constraints must be represented explicitly.
- Schema changes are managed through versioned migrations.
- Data imports and exports follow the platform validation, preview, confirmation and audit flow.
- Business history required by the domain must not be lost through destructive updates.
- Sensitive data must follow the security and access conventions.

## Identifier and timestamp direction

The source template uses UUID as an example identifier. The final identifier strategy is not yet decided. Time-related data must preserve enough information for audit, ordering and tenant-local interpretation; timezone handling is a technical decision to be documented.

## Tenant safety

- Tenant filtering is mandatory for tenant-owned data.
- Background work, reports, exports and administrative tools must preserve tenant context.
- Cross-tenant access is never implied by a missing filter.
- Referential relationships must not create a path around tenant isolation.

## Migration and integrity

- A migration must be reviewable and repeatable according to the eventual deployment process.
- Required fields and relationships must be introduced in a way that preserves existing data.
- Unique constraints must state whether uniqueness is platform-wide or tenant-scoped.
- Deletion, archival and retention behavior must be defined by the owning module.

## Indexing and performance direction

Module data models should identify important lookup paths, tenant-scoped queries, time-based queries and reporting needs. Performance decisions should be based on measured access patterns rather than speculative indexing.

## Open Questions

- Which database technology and deployment topology will be selected?
- What identifier and timestamp conventions are mandatory?
- Which records require soft deletion, archival or immutable history?
- What retention and restore guarantees are required for the first pilot?
- Which reporting workloads need a separate read model later?

