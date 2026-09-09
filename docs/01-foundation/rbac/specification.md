# RBAC Specification

Status: DRAFT

## Purpose

Define the role, permission and scope model used to authorize platform actions consistently across modules and channels.

## Scope

This specification defines the conceptual authorization model. Detailed permission names and the complete matrix will be added after Phase 1 actions and ownership are confirmed.

## Core concepts

- User.
- Role.
- Permission.
- RolePermission.
- UserRole.
- Scope.

A permission represents an allowed action on a resource. A role groups permissions. A user receives roles within an applicable tenant and scope.

## Initial actor roles

- System Administrator.
- School Administrator.
- Ban Giám hiệu.
- Tổ trưởng chuyên môn.
- Giáo viên chủ nhiệm.
- Giáo viên bộ môn.
- Học sinh.
- Phụ huynh or guardian.
- Nhân viên nghiệp vụ.

These are product roles, not necessarily the final technical role records.

## Scope levels

The current roadmap identifies these possible scopes:

- Platform or all schools.
- One school.
- Department.
- Grade.
- Class.
- Subject.
- Individual student.

An action is allowed only when the user's role and scope both permit it.

## Core rules

- Authentication establishes the actor; RBAC establishes authorization.
- Tenant isolation is a mandatory boundary for tenant-scoped roles.
- A teacher's access to attendance, grades and student lists is constrained by teaching assignment or homeroom responsibility, unless a broader role grants access.
- A parent can access only linked children.
- A student can access only permitted self-service information.
- Sensitive actions such as grade changes, permission changes, imports and student-data changes require explicit permission and audit.
- Modules declare the permissions they need; they do not implement private authorization engines.

## Permission model direction

Permission naming, inheritance, delegation, conflict handling and scope evaluation require a dedicated follow-up specification. Until then, module documents must reference this capability and record their required access as an Open Question or Proposed item.

## Open Questions

- Are roles tenant-defined, system-defined or a combination?
- How are multiple roles combined when scopes conflict?
- Is there explicit deny behavior?
- How are temporary assignments and delegation handled?
- Which actions require elevated or dual approval?
- What is the canonical permission naming scheme?

