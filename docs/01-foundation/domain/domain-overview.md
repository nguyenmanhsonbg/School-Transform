# Domain Overview

Status: DRAFT

## Purpose

Describe the conceptual business landscape of the School Digital Platform and establish the first domain boundaries before module specifications are created.

## Scope

This document covers the domain groups shared by the roadmap. It does not define database tables, API contracts or UI behavior.

## Domain landscape

### Platform Foundation

Tenant, identity, access control, audit, file, notification and configuration capabilities provide shared support for every phase.

### School Structure

School organization, departments, grades, classes, rooms, teachers, students and parents describe the people and structure of a school.

### Academic Planning

Academic years, terms, subjects, teaching assignments and timetables describe what is planned and who is responsible for teaching it.

### Academic Execution

Attendance and grading record what happens during teaching and learning.

### School Operations

Requests, forms, approvals, announcements, events, examinations, rewards, discipline and management reporting extend the core operating model in Phase 2.

### Digital School Services

Admission, tuition, library, assets, LMS, online examination, clubs, extracurricular activities and integrations extend the platform in Phase 3.

### AI School

The AI Platform and its assistants, analytics and risk capabilities consume controlled platform data in Phase 4. AI is not a replacement for the core data or authorization model.

## Core actors

- System Administrator.
- School Administrator.
- Ban Giám hiệu.
- Tổ trưởng chuyên môn.
- Giáo viên chủ nhiệm.
- Giáo viên bộ môn.
- Học sinh.
- Phụ huynh hoặc người giám hộ.
- Nhân viên nghiệp vụ.
- External systems and integration operators.

## Domain relationships at a high level

The school and academic structure provides the context for people and learning activities. Academic planning connects teachers, subjects, classes and time. Attendance and grading record academic execution. Foundation capabilities apply across all of these relationships.

## Boundary principles

- A school is a business organization; a tenant is the initial customer and isolation boundary.
- A module owns its business rules and data meaning.
- Shared capabilities provide reusable services without taking ownership of unrelated business rules.
- Applications are interaction channels, not separate domain boundaries.
- Later workflow and AI capabilities must use existing identity, permission, audit and data boundaries.

## Open Questions

- Whether School and Tenant remain one-to-one when a future customer manages multiple schools.
- Whether Organization is one module or a group of School, Department, Grade, Class and Room capabilities.
- Whether Parent is modeled as a domain person, an account relationship, or both.
- Which reporting capabilities belong to a domain module versus a shared reporting capability.

