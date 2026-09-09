# Domain Boundaries

Status: DRAFT

## Purpose

Define the first ownership boundaries between shared foundation capabilities and business modules.

## Boundary map

| Boundary | Owns | Does not own |
|---|---|---|
| Tenant | Tenant lifecycle and tenant context | Business rules of school modules |
| Identity | Account lifecycle and authentication context | Role policy and module business decisions |
| RBAC | Roles, permissions and access scopes | User-facing workflow or academic data |
| Organization | School structure and organizational relationships | Authentication or generic access control |
| Academic Year | Years, terms and academic calendar | Student grades or attendance records |
| People | Student, parent, teacher and relevant relationships | Generic account security |
| Academic Planning | Subjects, assignments and timetables | Attendance outcomes or grade calculations |
| Academic Execution | Attendance and grading | Generic notification delivery |
| Audit | Significant action history | The business transaction that caused the action |
| File Management | File lifecycle, metadata and access linkage | The business meaning of an attachment |
| Notification | Delivery and read state | The source event or business decision |
| Configuration | Declared configurable values and versions | Arbitrary customer-specific code |

## Later boundaries

- Request / Workflow Platform owns reusable request and approval mechanics.
- Request types own the business meaning of a particular request.
- Integration Hub owns external connection concerns and operational records.
- AI Platform owns shared AI access, evaluation, audit and tool boundaries.
- Individual AI assistants own their use cases, not the underlying source-of-truth data.

## Dependency direction

Business modules may use shared foundation capabilities through explicit contracts. A module must not create a private copy of a shared permission, audit, notification, configuration or file-management engine.

Module-to-module dependencies must follow the approved domain dependency map. A consumer may use another module's published concepts without taking ownership of its private business rules.

## Channel boundary

Admin Web, Teacher Web, Student App and Parent App are channels. They may have different navigation and experiences, but they must not define duplicate Student, Attendance, Grades or Notification business rules.

## Open Questions

- Whether Organization is a single boundary or several Phase 1 modules.
- Whether Reporting is a shared read capability or belongs to each source domain.
- Which module owns parent communication preferences and notification targeting.
- What contract style is required between modules in the initial monolith.

