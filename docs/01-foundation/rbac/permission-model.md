# Permission Model

Status: DRAFT

## Purpose

Define the authorization tuple and evaluation concepts that module specifications must use before a complete permission matrix is created.

## Scope

This document refines the [RBAC Specification](specification.md) at the model level and follows [Multi-tenancy](../multi-tenancy/specification.md) and [Security Conventions](../../90-cross-cutting/security.md). It does not finalize permission names, inheritance, deny behavior or every module action.

## Permission tuple

A permission is evaluated as:

Resource + Action + Tenant Context + Scope

Examples of resources include student, attendance, grade, timetable and notification. Examples of actions include view, create, update, delete, import, export, lock and unlock.

## Role assignment

A user receives one or more roles. A role groups permissions and is applied within an applicable tenant and scope. The source roadmap identifies scopes at platform, school, department, grade, class, subject and individual-student levels.

## Proposed evaluation order

1. Establish the authenticated user.
2. Establish the target tenant.
3. Resolve roles assigned in that tenant or platform context.
4. Resolve the resource and requested action.
5. Evaluate the role permission at the target scope.
6. Apply any sensitive-action or ownership constraint.
7. Record the action when it is significant.

This is a proposed behavioral sequence and must be confirmed with the final policy model.

## Domain examples

- A subject teacher may view the student list for assigned classes.
- A subject teacher may record attendance or grades only for the relevant teaching assignment.
- A homeroom teacher may receive broader access for the assigned class.
- A parent may view only linked children.
- A student may view only permitted self-service information.
- A school administrator may manage school-scoped records according to assigned permissions.

These examples express source direction; the final permission codes and scope rules remain to be defined.

## Sensitive actions

Grade changes, grade unlocks, permission changes, student-data changes, imports, exports and cross-tenant administration require explicit permission and audit.

## Matrix boundary

The complete permission matrix is intentionally deferred until Phase 1 module actions, ownership and naming are stable. Module specifications must reference this capability rather than creating private permission systems.

## Open Questions

- Are roles system-defined, tenant-defined or a combination?
- Does the model support explicit deny or only positive grants?
- How are multiple roles and overlapping scopes combined?
- How are temporary assignments, delegation and emergency access handled?
- What is the canonical resource-action permission naming scheme?
- Which actions require elevated or dual approval?
