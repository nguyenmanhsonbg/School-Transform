# Product Roadmap

Status: DRAFT

## Purpose

Describe the business milestones and their dependency-oriented progression without treating a Phase as a single development unit.

## Roadmap

| Phase | Name | Business outcome |
|---|---|---|
| Phase 0 | Platform Foundation | A secure, tenant-aware and reusable platform baseline |
| Phase 1 | School Core MVP | A THPT can operate its basic academic cycle end-to-end |
| Phase 2 | School Operations | Administrative and coordination workflows move from paper, spreadsheets and fragmented channels into the platform |
| Phase 3 | Digital School Platform | The platform expands into broader school services and integrations |
| Phase 4 | AI School | AI assists management, teaching, learning and parent support on top of mature platform data |

## Phase dependencies

### Phase 0 — Foundation

Domain model, multi-tenancy, identity, RBAC, audit, file management, notification, configuration and integration preparation are shared by later phases. In the documentation tree, this is represented by `01-foundation` rather than a closed phase-0 folder.

### Phase 1 — School Core MVP

The core dependency path is:

School and academic structure → academic year → class → student and teacher → subject → teaching assignment → timetable → attendance and grading.

Notification, import/export, audit and reporting support the end-to-end flow. Admin Web, Teacher Web, Student App and Parent App are channels over the underlying modules.

### Phase 2 — School Operations

The shared Request / Workflow Platform should precede request types such as leave, permission, information correction and activity registration.

### Phase 3 — Digital School Platform

Modules should remain independently specifiable and configurable by tenant. The Integration Hub provides the common connection and operational controls for external systems.

### Phase 4 — AI School

The AI Platform should precede individual assistants and analytics capabilities. AI depends on sufficient data, digitized workflows, clear permissions and auditability.

## Phase 0 exit criteria

Phase 0 is ready to hand off to dependent foundation and School Core work when all of the following can be verified:

- At least two independent tenants can be created.
- A user operating in tenant A is denied access to tenant B.
- RBAC evaluates the configured roles and scopes.
- Major sensitive actions are recorded with the shared audit event minimum.
- An authenticated API is available for platform consumers.
- Tenant and module configuration can be managed through the foundation capability.
- The import/export framework supports its planned baseline flow.
- A deployment pipeline to UAT is available.

## Release direction

- Release 0.x: internal development.
- Release 1.0: School Core MVP.
- Release 1.x: pilot improvements.
- Release 2.0: School Operations.
- Release 3.0: Digital School Platform.
- Release 4.0: AI capabilities.

## Pilot direction

After Phase 1, the product should be validated with one to three THPT design partners. Pilot feedback is classified before becoming Core, Configuration, Shared Module, Integration or Custom.

## Open Questions

- The precise sequencing of Phase 1 modules must follow the approved dependency map.
- The boundary between Phase 1 Reporting and later Management Reporting needs confirmation.
- Integration preparation in Phase 0 and the Integration Hub in Phase 3 need separate capability boundaries.
