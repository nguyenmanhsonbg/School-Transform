# Modular Architecture

Status: DRAFT

## Purpose

Define module grouping and dependency guardrails for the Modular Monolith baseline.

## Module groups

### Shared foundation modules

- Tenant.
- Identity.
- RBAC.
- Audit.
- File Management.
- Notification.
- Configuration.

### Phase 1 business modules

- Organization.
- Academic Year.
- Student.
- Parent.
- Teacher.
- Subject.
- Teaching Assignment.
- Timetable.
- Attendance.
- Grading.
- Reporting where it is confirmed as a module.

### Later modules

- Request / Workflow Platform and request types.
- Communication enhancements.
- Admission, Tuition, Library, Asset Management, LMS, Online Exam, Clubs and Integration Hub.
- AI Platform and AI feature modules.

## Dependency guardrails

- Shared foundation capabilities are reusable dependencies, not duplicated business modules.
- Each business module owns its business rules and publishes only the concepts other modules need.
- Cross-module access must use explicit module contracts rather than relying on undocumented private details.
- The dependency map must follow domain meaning, not application navigation.
- Circular dependencies require an explicit decision and review.
- Channel applications depend on module capabilities; module business rules do not depend on a specific channel.

## Phase 1 dependency direction

The current conceptual order is:

School structure → Academic Year → Class → Student and Teacher → Subject → Teaching Assignment → Timetable → Attendance and Grading.

Parent, Notification, Audit, Import/Export and Reporting support this flow but must not create duplicate ownership of its core rules.

## Evolution path

The monolith may later extract a module into a separate service if scale, deployment independence, team ownership, compliance or another demonstrated requirement justifies it. Extraction is not an MVP assumption.

## Open Questions

- Whether Organization, Class and Room are separate modules or one structural boundary.
- The exact contract mechanism between modules.
- Which read models or reporting queries need isolation from transactional modules.
- What evidence would justify extracting a module from the monolith.

