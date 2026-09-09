# Tenant Isolation

Status: DRAFT

## Purpose

Define how the platform must preserve the boundary between school tenants across business data, platform capabilities and operational flows.

## Scope

This document refines the isolation rules from the [Multi-tenancy Specification](specification.md). It also follows [Security Conventions](../../90-cross-cutting/security.md). It does not choose a physical database topology.

## Confirmed requirements

- Each school is an initial tenant.
- Core business data is associated with a tenant.
- Tenant-specific configuration may differ.
- A user operating in tenant A must not access tenant B by default.
- Audit records must preserve tenant context.

## Protected surfaces

Tenant isolation applies to:

- API reads and writes.
- Module-to-module operations.
- Background jobs.
- Imports and exports.
- Reports and dashboards.
- Files and attachments.
- Notifications and recipient selection.
- Audit records.
- Integration requests and callbacks.

## Proposed enforcement model

Every operation that handles tenant-owned data should establish tenant context before authorization and business execution. The owning capability should reject an operation when the context is absent, invalid or inconsistent with the target data.

Tenant context must not be inferred only from a client-provided identifier. A platform-level actor may receive an explicitly authorized cross-tenant context only through a separately controlled operation.

## Cross-tenant operations

Cross-tenant administration and reporting are not part of the initial default behavior. If introduced, each operation must define:

- The platform role that may perform it.
- The permitted target tenants.
- The reason or operational purpose.
- The audit fields and retention behavior.
- The response and export restrictions.

## Failure behavior

Proposed behavior is to deny access when tenant context cannot be established or when the target object belongs to another tenant. The API should return a safe authorization or not-found result without revealing another tenant's existence.

## Verification scenarios

- Create two tenants and identical-looking records in each.
- Verify tenant A cannot read, update, delete, export or attach files to tenant B records.
- Verify background and integration flows preserve the originating tenant.
- Verify reports and notifications do not mix tenant data.
- Verify tenant context appears in significant audit events.

## Open Questions

- Which layer is the final enforcement point for each operation type?
- Will isolation use a shared database, tenant schema, database-per-tenant or a hybrid?
- Can any reference data be platform-global?
- What is the approved behavior for a user linked to multiple tenants?
- What cross-tenant operations, if any, are required for the first pilot?
