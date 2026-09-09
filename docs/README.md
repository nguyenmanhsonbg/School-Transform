# School Digital Platform Documentation

Status: DRAFT

## Purpose

This directory is the working documentation set for the School Digital Platform. It separates product direction, foundation capabilities, phase modules, cross-cutting conventions, architectural decisions and specification tracking.

The documentation structure follows:

- [Documentation & Specification Structure](../school-platform-documentation-specification.md)
- [THPT Phase Specification](../THPT_Digital_Transformation_Phase_Specification.md)

The first document is authoritative for how documentation is organized. The second is authoritative for the current product context, scope and roadmap.

## Reading order

Before designing or implementing a module, read:

1. Product vision, scope, principles, glossary and roadmap.
2. Domain model and domain boundaries.
3. System context and architecture documents.
4. Multi-tenancy, identity and RBAC specifications.
5. Relevant cross-cutting conventions.
6. The local module specification and its progressively added detail documents.

## Documentation rules

- Phase is a business milestone. Module or Capability is the specification and development unit.
- Business rules belong to the module that owns them.
- A business rule has one authoritative source; other documents link to it.
- Application channels describe interface and actor experience, not duplicated business domains.
- Shared capabilities such as permission, audit, notification, configuration and file management must be reused.
- Business specifications remain implementation-neutral unless a technical decision is required.
- Unresolved matters must be marked as Open Question or Proposed / To Be Confirmed.
- Architectural decisions that materially affect the system are recorded as ADRs.
- New detail documents are added progressively when they have practical value.
- A specification is not READY_FOR_DEV merely because its file exists.

## Status vocabulary

Specifications use:

`DRAFT`, `READY_FOR_DESIGN`, `READY_FOR_DEV`, `IN_DEVELOPMENT`, `READY_FOR_TEST`, `DONE`

ADR files use their own decision status, such as Proposed, Accepted or Superseded.

## Naming

Folders and ordinary Markdown files use lowercase kebab case. ADR files use the format `ADR-XXX-name.md`.

## Change discipline

When a business rule changes, update its authoritative specification and review affected dependencies. Do not silently introduce a conflicting rule in another module.

## Open Questions

- Whether this documentation set will be maintained in English, Vietnamese or a bilingual format.
- Which approval and ownership workflow will be used for specification status changes.
