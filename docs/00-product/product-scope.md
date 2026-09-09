# Product Scope

Status: DRAFT

## Purpose

Define the product boundary across the roadmap and the initial School Core MVP.

## Product scope

### In scope across the roadmap

- Product and domain foundation.
- Multi-tenancy, identity and access control.
- School structure, academic planning and academic execution.
- School operations, requests and approvals.
- Digital school services and external integrations.
- Shared platform capabilities required by the above.
- AI Platform and AI-assisted capabilities in the later phase.

### Initial target

The initial target is a reusable platform for multiple THPT schools. A single customer-specific workflow must not determine the core product unless it is classified and accepted as a broadly reusable capability.

## Phase scope

### Phase 0 — Platform Foundation

Tenant management, identity and authentication, RBAC, audit, file management, notification framework, configuration framework and integration preparation.

### Phase 1 — School Core MVP

Organization, academic year, class, student, parent, teacher, subject, teaching assignment, timetable, attendance, grading, notification, reporting and the relevant web/mobile channels.

The success criterion is an end-to-end academic operating flow that can be demonstrated and piloted.

### Phase 2 — School Operations

Request and workflow capabilities, forms, approvals, leave and permission requests, announcements, events, exam schedule, rewards and discipline, communication and management reporting.

### Phase 3 — Digital School Platform

Admission, tuition and payment, library, asset management, LMS, online exam, clubs, extracurricular activities and an integration hub.

### Phase 4 — AI School

A shared AI Platform followed by management, teacher, student and parent assistants, learning analytics, student risk detection and report generation.

## Scope classification for new requirements

Every new customer request should be evaluated as:

| Classification | Meaning |
|---|---|
| Core | Common to most THPT schools and belongs in the product core |
| Configuration | Can be handled by tenant or module configuration |
| Shared Module | Reusable capability for multiple schools |
| Integration | Best handled through an external system connection |
| Custom | Customer-specific and isolated from the core |

## Out of scope for the first MVP

- Full enterprise HRM and payroll.
- General accounting.
- Advanced LMS and complete online examination.
- Library and asset management.
- Complex payment gateway ecosystem.
- Comprehensive admission platform.
- AI chatbot for the entire school.
- AI-based grading or disciplinary conclusions.

## Open Questions

- Whether the Phase 1 organization capability is documented as one module or as several related modules.
- Whether reporting is a Phase 1 module or a cross-cutting consumer of domain data.
- Whether Student App and Parent App share one mobile application.

