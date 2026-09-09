# API Conventions

Status: DRAFT

## Purpose

Define shared API behavior for web channels, mobile channels and integrations.

## Scope

This document covers API principles and externally visible conventions. It does not define module-specific endpoints or implementation frameworks.

## Principles

- Important platform capabilities are available through APIs.
- APIs are versioned. The current documentation examples use a versioned path such as /api/v1.
- Resource and action names use the glossary and owning module terminology.
- API contracts must preserve tenant and authorization boundaries.
- Validation and error behavior should be consistent across modules.
- API changes must be reviewed against consumers and documented dependencies.

## Request context

An authenticated request should establish:

- Actor identity.
- Tenant context.
- Applicable roles and permission scopes.
- Correlation ID for tracing the request.

The API must not accept a client-supplied tenant context as the sole basis for access.

## Resource behavior

- Use resource-oriented operations where they express the business action clearly.
- Use explicit action operations when a business transition cannot be represented safely as a generic update.
- Apply pagination to collection responses.
- Define filtering and sorting deliberately for each collection.
- Make imports and other potentially long-running operations observable rather than blocking the primary request unnecessarily.

## Validation and errors

- Validate input at the API boundary and again at the owning business capability where necessary.
- Return a stable error shape with a machine-readable code, human-readable message, field or object details when relevant, and correlation ID.
- Do not expose credentials, internal stack traces or sensitive tenant information in errors.
- Distinguish validation, authentication, authorization, not-found, conflict and operational failures.

## Audit and idempotency

Sensitive mutations, imports, exports and authorization changes must be auditable. Operations that may be retried or submitted more than once should define idempotency behavior in their module specification.

## Open Questions

- What exact error response schema will be standardized?
- Which HTTP methods and status-code conventions are mandatory?
- Which operations require idempotency keys?
- How will API deprecation and backward compatibility be managed?

