# Domain Model

Status: DRAFT

## Purpose

Define the initial conceptual model and relationships that later module specifications must use consistently.

## Scope

This is a business-level model. Field types, storage technology, indexes and API representations belong in later data-model and technical documents.

## Entity groups

| Group | Concepts |
|---|---|
| Platform | Tenant, User, Role, Permission, RolePermission, UserRole, Scope, Audit Record, File, Notification, Configuration |
| School structure | School, Department, Grade, Class, Room |
| People | Student, Student Class History, Student Status History, Parent, Student Parent, Teacher, Teacher Subject, Teacher Department, Homeroom Assignment |
| Academic calendar | Academic Year, Term, Academic Calendar |
| Academic planning | Subject, Grade Subject, Teaching Assignment, Time Slot, Timetable, Timetable Entry |
| Academic execution | Attendance Session, Attendance Record, Attendance Reason, Grade Type, Assessment, Student Score, Grade Lock |

## Core relationships

| Relationship | Meaning |
|---|---|
| Tenant to School | The initial model treats one school as one tenant; future multi-school relationships remain open |
| School to Department, Grade, Class and Room | A school owns or organizes these structural concepts |
| Class to Student | A class groups students for a configured academic context |
| Student to Parent | A student may have multiple guardians, and a parent may be linked to multiple students |
| Teacher to Department and Subject | A teacher may belong to departments and have teachable subjects |
| Academic Year to Term | A year contains a tenant-configurable number of terms |
| Teaching Assignment | Connects Teacher, Subject, Class, Academic Year and Term |
| Timetable Entry | Places a planned teaching assignment into a time slot and, when applicable, a room |
| Attendance Session and Record | A teaching session records attendance for the relevant students |
| Grade Type, Assessment and Student Score | A configured assessment process records results for students |

## Platform relationships

- Users receive roles and permissions within an applicable scope.
- Core business objects belong to a tenant unless explicitly defined as platform-global.
- Audit records refer to significant actions and affected objects. Their minimum event fields are defined in [Security Conventions](../../90-cross-cutting/security.md).
- Files are reusable attachments or managed resources and do not own the business meaning of their parent object.
- Notifications deliver information to selected recipients and do not replace the source business record.
- Configuration changes behavior within a declared tenant, module or academic context.

## Modeling rules

- Use the glossary terms consistently.
- Keep business identity separate from presentation or channel-specific identifiers.
- Preserve history where the roadmap explicitly requires it, such as student class and status history.
- Do not hard-code the number of academic terms or grade types.
- Do not place permission or notification rules inside unrelated entity definitions.

## Open Questions

- Whether School is always represented separately from Tenant in the first implementation.
- Whether a person can hold multiple account identities across tenants.
- Whether Class membership is scoped to Academic Year, Term, or both.
- Whether a Room is part of Organization or Timetable ownership.
- Whether Grade is reserved for assessment result, academic level, or both with explicit context.
