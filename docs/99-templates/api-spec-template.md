# [Module Name] API

Document Type: Template
Default Status: DRAFT

## Purpose

Provide a progressive structure for documenting a module API after the business capability and permission model are clear.

## Metadata

- Phase: [Phase number or Foundation]
- Module: [Name]
- Owner: [Owner]
- Status: DRAFT

## API principles

Follow the API and Security Conventions at docs/90-cross-cutting/api-conventions.md and docs/90-cross-cutting/security.md, together with the owning module specification. After copying this template into a module folder, replace these paths with links relative to the destination file.

## Classification

### Confirmed contract

- [Contract already approved]

### Proposed contract

- [Contract to be confirmed]

## Endpoint

### [METHOD] /api/v1/[resource]

#### Purpose

[Business outcome of the endpoint.]

#### Permission

- Resource: [Resource]
- Action: [Action]
- Scope: [Scope]

#### Tenant and actor context

[Required tenant, identity and authorization behavior.]

#### Request

[Parameters, body, validation and idempotency behavior.]

#### Response

[Success status and response shape.]

#### Errors

[Validation, authentication, authorization, not-found, conflict and operational errors.]

#### Audit

[Whether the action is significant and what is recorded.]

## Compatibility

[Versioning, deprecation and consumer impact.]

## Open Questions

- [Unresolved API contract decision]
