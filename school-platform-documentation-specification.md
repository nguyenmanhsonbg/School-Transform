# School Digital Platform — Documentation & Specification Structure

**Version:** 1.0  
**Status:** Baseline  
**Purpose:** Quy định cấu trúc tài liệu và cách quản lý specification cho dự án Chuyển đổi số Trường học.

---

# 1. Mục tiêu

Tài liệu này định nghĩa cấu trúc thư mục `docs/` và nguyên tắc xây dựng specification cho School Digital Platform.

Mục tiêu chính:

- Phát triển sản phẩm theo từng Phase.
- Cho phép hoàn thiện specification dần theo từng module.
- Không yêu cầu toàn bộ specification của một Phase phải hoàn thành trước khi coding.
- Cho phép BA/Product, Backend, Frontend, Mobile, Tester làm song song.
- Đảm bảo các quyết định về domain, kiến trúc và business rule không bị phân tán.
- Hỗ trợ tốt cho AI-assisted development như ChatGPT, Codex, Claude, GitHub Copilot.
- Giữ khả năng mở rộng từ MVP thành Digital School Platform và AI School.

Nguyên tắc cốt lõi:

> **Phase là business milestone. Module/Capability mới là đơn vị triển khai development.**

---

# 2. Product Roadmap

## Phase 0 — Product Foundation

Các capability nền tảng:

- Domain Model
- Multi-tenancy
- Identity
- RBAC
- Audit Log
- File Management
- Notification Framework
- Configuration Framework

---

## Phase 1 — School Core MVP

Các module nghiệp vụ cốt lõi:

- Student
- Teacher
- Class
- Subject
- Academic Year
- Teaching Assignment
- Timetable
- Attendance
- Grades

Ứng dụng:

- Web Admin
- Teacher Web
- Student App
- Parent App

Kết quả mong muốn:

- Có thể demo end-to-end.
- Có thể pilot tại trường THPT thực tế.
- Có bộ School Core đủ để phát triển tiếp các module sau.

---

## Phase 2 — School Operations

Các module:

- Leave Request
- Permission Request
- Forms
- Approval Workflow
- Announcements
- Events
- Exam Schedule
- Rewards & Discipline
- Management Reporting

Định hướng:

Các nghiệp vụ đơn từ và phê duyệt nên ưu tiên xây dựng dựa trên một **Request / Workflow Platform** dùng chung thay vì phát triển từng quy trình riêng biệt.

---

## Phase 3 — Digital School Platform

Các module:

- Admission
- Tuition
- Library
- Asset Management
- LMS
- Online Exam
- Clubs
- Extracurricular Activities
- Third-party Integrations

---

## Phase 4 — AI School

Các capability:

- AI Teacher Assistant
- AI Management Assistant
- AI Student Assistant
- Learning Analytics
- Student Risk Detection
- AI Report Generation
- AI Parent / Customer Support

Phase này cần có một **AI Platform Layer** dùng chung cho các AI feature.

---

# 3. Cấu trúc thư mục `docs/`

```text
docs/
│
├── README.md
│
├── 00-product/
│   ├── product-vision.md
│   ├── product-scope.md
│   ├── product-principles.md
│   ├── stakeholders.md
│   ├── glossary.md
│   └── roadmap.md
│
├── 01-foundation/
│   ├── architecture/
│   │   ├── system-context.md
│   │   ├── system-architecture.md
│   │   ├── modular-architecture.md
│   │   └── deployment-architecture.md
│   │
│   ├── domain/
│   │   ├── domain-overview.md
│   │   ├── domain-model.md
│   │   └── domain-boundaries.md
│   │
│   ├── multi-tenancy/
│   │   ├── specification.md
│   │   ├── tenant-isolation.md
│   │   └── data-strategy.md
│   │
│   ├── identity/
│   │   ├── specification.md
│   │   ├── authentication.md
│   │   └── account-lifecycle.md
│   │
│   ├── rbac/
│   │   ├── specification.md
│   │   ├── permission-model.md
│   │   └── permission-matrix.md
│   │
│   ├── audit/
│   │   └── specification.md
│   │
│   ├── file-management/
│   │   └── specification.md
│   │
│   ├── notification/
│   │   └── specification.md
│   │
│   └── configuration/
│       └── specification.md
│
├── 02-phase-1-school-core/
│   ├── README.md
│   │
│   ├── student/
│   │   ├── specification.md
│   │   ├── business-rules.md
│   │   ├── user-flows.md
│   │   ├── data-model.md
│   │   ├── api.md
│   │   └── acceptance-criteria.md
│   │
│   ├── teacher/
│   │   └── ...
│   │
│   ├── classroom/
│   │   └── ...
│   │
│   ├── subject/
│   │   └── ...
│   │
│   ├── academic-year/
│   │   └── ...
│   │
│   ├── teaching-assignment/
│   │   └── ...
│   │
│   ├── timetable/
│   │   └── ...
│   │
│   ├── attendance/
│   │   └── ...
│   │
│   ├── grades/
│   │   └── ...
│   │
│   └── applications/
│       ├── admin-web.md
│       ├── teacher-web.md
│       ├── student-app.md
│       └── parent-app.md
│
├── 03-phase-2-school-operations/
│   ├── README.md
│   ├── request-workflow/
│   │   ├── specification.md
│   │   ├── request-type.md
│   │   ├── form-definition.md
│   │   ├── approval-workflow.md
│   │   └── business-rules.md
│   ├── leave-request/
│   ├── permission-request/
│   ├── announcements/
│   ├── events/
│   ├── exam-schedule/
│   ├── rewards-discipline/
│   └── management-reporting/
│
├── 04-phase-3-digital-school/
│   ├── README.md
│   ├── admission/
│   ├── tuition/
│   ├── library/
│   ├── asset-management/
│   ├── lms/
│   ├── online-exam/
│   ├── clubs/
│   ├── extracurricular/
│   └── integrations/
│
├── 05-phase-4-ai-school/
│   ├── README.md
│   │
│   ├── ai-platform/
│   │   ├── architecture.md
│   │   ├── llm-provider.md
│   │   ├── knowledge-base.md
│   │   ├── rag.md
│   │   ├── tool-access.md
│   │   ├── authorization.md
│   │   ├── prompt-management.md
│   │   ├── ai-audit.md
│   │   └── evaluation.md
│   │
│   ├── teacher-assistant/
│   ├── management-assistant/
│   ├── student-assistant/
│   ├── learning-analytics/
│   ├── student-risk/
│   ├── report-generation/
│   └── parent-support/
│
├── 90-cross-cutting/
│   ├── api-conventions.md
│   ├── database-conventions.md
│   ├── security.md
│   ├── logging-monitoring.md
│   ├── error-handling.md
│   ├── testing-strategy.md
│   ├── frontend-conventions.md
│   ├── mobile-conventions.md
│   └── integration-principles.md
│
├── 91-decisions/
│   ├── README.md
│   ├── ADR-001-modular-monolith.md
│   ├── ADR-002-multi-tenancy.md
│   ├── ADR-003-authentication.md
│   └── ...
│
├── 92-spec-status/
│   ├── specification-status.md
│   └── dependency-map.md
│
└── 99-templates/
    ├── module-spec-template.md
    ├── business-rule-template.md
    ├── api-spec-template.md
    ├── adr-template.md
    └── feature-template.md
```

---

# 4. Ý nghĩa từng nhóm thư mục

## 4.1 `00-product`

Chứa các tài liệu ở cấp độ sản phẩm.

Không phụ thuộc vào implementation cụ thể.

Bao gồm:

- Product Vision
- Product Scope
- Product Principles
- Stakeholders
- Glossary
- Roadmap

Các tài liệu trong nhóm này nên được đọc trước khi thiết kế module mới.

---

## 4.2 `01-foundation`

Chứa các platform capability được sử dụng xuyên suốt toàn bộ hệ thống.

Phase 0 được thể hiện dưới dạng `foundation` thay vì một phase đóng kín vì các capability như:

- Identity
- RBAC
- Multi-tenancy
- Audit
- Notification
- Configuration

sẽ tiếp tục được sử dụng và mở rộng trong mọi phase tiếp theo.

---

## 4.3 `02-phase-1-school-core`

Chứa School Core MVP.

Đây là phần tạo ra giá trị nghiệp vụ đầu tiên cho khách hàng và là milestone để có thể demo/pilot.

---

## 4.4 `03-phase-2-school-operations`

Chứa các nghiệp vụ vận hành trường học.

Các nghiệp vụ dạng:

- đơn từ,
- biểu mẫu,
- phê duyệt,
- xin phép,

nên ưu tiên xây dựng trên một `Request / Workflow Platform` dùng chung.

---

## 4.5 `04-phase-3-digital-school`

Chứa các bounded module lớn có khả năng phát triển tương đối độc lập.

Ví dụ:

- Tuition
- Library
- LMS
- Admission

Mỗi module vẫn nằm trong Modular Monolith ở giai đoạn đầu, nhưng có thể được tách thành service riêng trong tương lai nếu có nhu cầu thực tế.

---

## 4.6 `05-phase-4-ai-school`

AI feature không nên tự xây một AI stack riêng.

Tất cả AI feature sử dụng chung một AI Platform.

```text
                 AI Platform
                     │
        ┌────────────┼────────────┐
        │            │            │
        ▼            ▼            ▼
   Teacher AI     BGH AI      Student AI
```

AI Platform chịu trách nhiệm các capability chung như:

- LLM Provider
- RAG
- Knowledge Base
- Tool Access
- Authorization
- Prompt Management
- AI Audit
- Evaluation

---

## 4.7 `90-cross-cutting`

Chứa các quy chuẩn kỹ thuật áp dụng cho nhiều module.

Ví dụ:

- API conventions
- Database conventions
- Security
- Error handling
- Logging
- Testing

Không đặt các business specification cụ thể trong thư mục này.

---

## 4.8 `91-decisions`

Chứa Architecture Decision Records (ADR).

Ví dụ:

```text
ADR-001-modular-monolith.md
ADR-002-multi-tenancy.md
ADR-003-authentication.md
```

ADR giúp ghi lại:

- quyết định,
- lý do,
- phương án thay thế,
- ảnh hưởng.

---

## 4.9 `92-spec-status`

Dùng để theo dõi mức độ hoàn thiện specification.

Giúp BA/Product và Development làm song song mà không cần chờ cả Phase hoàn thiện.

---

## 4.10 `99-templates`

Chứa template chuẩn để tạo specification mới.

Mục tiêu:

- đồng nhất tài liệu,
- giảm thời gian soạn,
- hỗ trợ AI sinh specification theo cùng format.

---

# 5. Đơn vị Specification

Đơn vị specification chính của hệ thống là:

> **Module / Capability**

Không phải Phase.

Ví dụ:

```text
Phase 1
│
├── Student
├── Teacher
├── Class
├── Subject
├── Academic Year
├── Teaching Assignment
├── Timetable
├── Attendance
└── Grades
```

Mỗi module có thể được phát triển độc lập khi specification của module đó đạt trạng thái `READY_FOR_DEV`.

---

# 6. Cấu trúc chuẩn cho một Module

Ví dụ:

```text
attendance/
├── specification.md
├── business-rules.md
├── user-flows.md
├── data-model.md
├── api.md
└── acceptance-criteria.md
```

Không bắt buộc phải tạo toàn bộ file ngay từ đầu.

---

# 7. Progressive Specification

Specification được hoàn thiện dần theo tiến độ development.

## Stage 1

```text
student/
└── specification.md
```

## Stage 2

```text
student/
├── specification.md
├── business-rules.md
└── data-model.md
```

## Stage 3

```text
student/
├── specification.md
├── business-rules.md
├── data-model.md
└── api.md
```

## Stage 4

```text
student/
├── specification.md
├── business-rules.md
├── user-flows.md
├── data-model.md
├── api.md
└── acceptance-criteria.md
```

Nguyên tắc:

> Không tạo hàng loạt file rỗng chỉ để đủ cấu trúc.

Chỉ tạo file khi tài liệu đó bắt đầu có giá trị sử dụng.

---

# 8. Specification Status

Mỗi specification nên có một trạng thái.

```text
DRAFT

READY_FOR_DESIGN

READY_FOR_DEV

IN_DEVELOPMENT

READY_FOR_TEST

DONE
```

## DRAFT

Specification đang được phân tích.

Không nên dựa vào tài liệu này để phát triển chính thức.

---

## READY_FOR_DESIGN

Business scope và domain đã tương đối rõ.

Có thể bắt đầu technical design.

---

## READY_FOR_DEV

Đủ thông tin để Development bắt đầu coding.

---

## IN_DEVELOPMENT

Module đang được triển khai.

Specification vẫn có thể tiếp tục được refine.

---

## READY_FOR_TEST

Acceptance criteria và business rule đã đủ để Tester thực hiện kiểm thử.

---

## DONE

Module đã được release và specification phản ánh trạng thái hiện tại của sản phẩm.

---

# 9. Definition of Ready for Development

Một module không cần có 100% specification để bắt đầu code.

Tuy nhiên, trước khi chuyển sang `READY_FOR_DEV`, tối thiểu cần có:

- Purpose
- Scope
- Actors
- Core Use Cases
- Critical Business Rules
- Main Entities
- Permission Model
- Happy-path User Flow
- Main Dependencies

Không bắt buộc phải hoàn thiện:

- toàn bộ API specification,
- toàn bộ error cases,
- toàn bộ UI details,
- toàn bộ test case,
- toàn bộ edge cases.

Các phần trên có thể được hoàn thiện song song với development.

---

# 10. Template `specification.md`

```md
# [Module Name] Specification

Status: DRAFT
Phase: [Phase Number]
Module: [Module Name]
Owner: [Owner]

---

## 1. Purpose

Mô tả mục tiêu của module.

---

## 2. Scope

### In Scope

- ...

### Out of Scope

- ...

---

## 3. Actors

- ...

---

## 4. Use Cases

### [MODULE]-001

...

---

## 5. Business Rules

Xem:

business-rules.md

---

## 6. User Flows

Xem:

user-flows.md

---

## 7. Data Model

Xem:

data-model.md

---

## 8. Permission

...

---

## 9. Dependencies

Depends on:

- ...

Used by:

- ...

---

## 10. API

Xem:

api.md

---

## 11. Acceptance Criteria

Xem:

acceptance-criteria.md

---

## 12. Open Questions

- ...
```

---

# 11. Template `business-rules.md`

```md
# [Module Name] Business Rules

## BR-[MODULE]-001

### Rule

...

### Rationale

...

### Example

...

### Exception

...
```

---

# 12. Template `data-model.md`

```md
# [Module Name] Data Model

## Entities

### EntityName

Fields:

| Field | Type | Required | Description |
|---|---|---:|---|
| id | UUID | Yes | Primary identifier |
| ... | ... | ... | ... |

---

## Relationships

...

---

## Constraints

...

---

## Indexes

...

---

## Multi-tenancy Rules

...
```

---

# 13. Template `api.md`

```md
# [Module Name] API

## API Principles

Tuân thủ:

`docs/90-cross-cutting/api-conventions.md`

---

## GET /api/v1/...

### Permission

...

### Request

...

### Response

...

### Errors

...

---

## POST /api/v1/...

...
```

---

# 14. Template `acceptance-criteria.md`

```md
# [Module Name] Acceptance Criteria

## AC-001

Given ...

When ...

Then ...

---

## AC-002

Given ...

When ...

Then ...
```

---

# 15. Specification Status Tracking

File:

```text
docs/92-spec-status/specification-status.md
```

Ví dụ:

```md
# Specification Status

| Module | Phase | Spec | Domain | Rules | API | UI | Dev |
|---|---|---|---|---|---|---|---|
| Multi-tenancy | 0 | Done | Done | Done | N/A | N/A | Done |
| Identity | 0 | Done | Done | Done | Done | Done | In Progress |
| RBAC | 0 | Done | Done | Done | Done | N/A | Ready |
| Student | 1 | Done | Done | Done | Draft | Draft | Ready |
| Teacher | 1 | Done | Done | Done | Draft | Draft | Ready |
| Class | 1 | Done | Done | Done | Ready | Draft | Ready |
| Timetable | 1 | Draft | Draft | Draft | - | - | Blocked |
| Attendance | 1 | Done | Done | Done | Ready | Ready | Ready |
| Grades | 1 | Draft | Draft | Draft | - | - | Not Started |
```

---

# 16. Dependency Map

File:

```text
docs/92-spec-status/dependency-map.md
```

Phase 1 dependency có thể được mô hình hóa:

```text
School
    │
    ▼
Academic Year
    │
    ▼
Class
   / \
  ▼   ▼
Student Teacher
          │
          ▼
       Subject
          │
          ▼
Teaching Assignment
          │
          ▼
       Timetable
        /     \
       ▼       ▼
Attendance   Grades
```

Ví dụ specification:

```md
# Module Dependency

## Student

Depends on:

- School
- Academic Year
- Class

---

## Teacher

Depends on:

- School

---

## Teaching Assignment

Depends on:

- Teacher
- Subject
- Class
- Academic Year

---

## Timetable

Depends on:

- Teaching Assignment
- Class
- Subject
- Academic Year

---

## Attendance

Depends on:

- Student
- Class
- Teaching Assignment
- Timetable

---

## Grades

Depends on:

- Student
- Subject
- Teaching Assignment
- Academic Year
```

---

# 17. Domain grouping cho Phase 1

Về mặt conceptual domain, Phase 1 nên được nhìn theo 3 nhóm.

## School Structure

```text
School Structure
├── Academic Year
├── Class
├── Subject
├── Student
└── Teacher
```

## Academic Planning

```text
Academic Planning
├── Teaching Assignment
└── Timetable
```

## Academic Execution

```text
Academic Execution
├── Attendance
└── Grades
```

Không bắt buộc tạo thêm tầng folder này nếu làm cấu trúc tài liệu phức tạp hơn.

---

# 18. Application Channels

Các ứng dụng:

- Admin Web
- Teacher Web
- Student App
- Parent App

không phải là domain nghiệp vụ riêng biệt.

Ví dụ không nên tổ chức:

```text
Admin/
  Student Management

Teacher/
  Student Management

Parent/
  Student Management
```

Điều này sẽ duplicate specification.

Nên tổ chức business theo module:

```text
Student
├── create
├── update
└── view
```

và mapping quyền theo actor:

```text
Admin:
- create
- update
- view

Teacher:
- view assigned students

Student:
- view self

Parent:
- view children
```

Các application chỉ đóng vai trò channel/interface.

---

# 19. Phase 2 — Request / Workflow Platform

Các chức năng như:

- Đơn xin nghỉ
- Xin phép
- Biểu mẫu
- Phê duyệt

không nên được xây thành các engine riêng biệt.

Nên có capability chung:

```text
Request / Workflow Platform
│
├── Form Definition
├── Request
├── Request Type
├── Approval Workflow
├── Approval Step
├── Comment
├── Attachment
└── Notification
```

Sau đó các use case như:

```text
Leave Request
Permission Request
Information Correction
Club Registration
Extracurricular Registration
Teacher Leave
Certificate Request
```

được triển khai dưới dạng `Request Type`.

---

# 20. Phase 4 — AI Platform

AI Platform nên là capability dùng chung.

```text
AI Platform
│
├── LLM Provider
├── Knowledge Base
├── RAG
├── Tool Access
├── Authorization
├── Prompt Management
├── AI Audit
├── Evaluation
└── Monitoring
```

AI feature:

```text
AI Platform
    │
    ├── Teacher Assistant
    ├── Management Assistant
    ├── Student Assistant
    ├── Learning Analytics
    ├── Student Risk Detection
    ├── Report Generation
    └── Parent Support
```

---

# 21. Minimum Documentation Baseline trước khi coding

Không cần hoàn thiện toàn bộ `docs/` trước khi coding.

Trước khi bắt đầu Phase 0, tối thiểu nên có:

```text
docs/

00-product/
├── product-vision.md
├── product-scope.md
├── glossary.md
└── roadmap.md

01-foundation/
├── domain/
│   └── domain-model.md
│
├── multi-tenancy/
│   └── specification.md
│
├── identity/
│   └── specification.md
│
└── rbac/
    └── specification.md

90-cross-cutting/
├── api-conventions.md
├── database-conventions.md
└── security.md
```

Sau khi các tài liệu trên đủ rõ có thể bắt đầu coding:

```text
Tenant
↓
Identity
↓
RBAC
```

Trong khi Development triển khai, Product/BA có thể tiếp tục hoàn thiện:

```text
Audit
File Management
Notification
Configuration
```

---

# 22. Development Flow

Luồng mong muốn:

```text
Product Vision
      │
      ▼
Product Scope
      │
      ▼
Domain Model
      │
      ▼
Phase
      │
      ▼
Module
      │
      ▼
Specification
      │
      ▼
READY_FOR_DEV
      │
      ▼
Development
      │
      ├──────────► Specification Refinement
      │
      ▼
READY_FOR_TEST
      │
      ▼
Testing
      │
      ▼
DONE
```

Specification và coding có thể chạy song song.

---

# 23. Project Root Recommendation

Cấu trúc root đề xuất:

```text
school-platform/
│
├── README.md
├── AGENTS.md
├── CONTRIBUTING.md
│
├── docs/
│   └── ...
│
├── backend/
│
├── admin-web/
│
├── teacher-web/
│
├── mobile-app/
│
├── infrastructure/
│
├── scripts/
│
└── docker/
```

Nếu Student và Parent sử dụng chung một application:

```text
mobile-app/
```

Role và permission sẽ quyết định UI.

Nếu có lý do business hoặc distribution riêng mới tách:

```text
student-app/
parent-app/
```

---

# 24. `AGENTS.md`

Nếu sử dụng AI-assisted development, nên tạo file `AGENTS.md` ở root repository.

Ví dụ:

```md
# AI Development Instructions

Before modifying code, read:

1. docs/00-product/product-vision.md
2. docs/00-product/product-scope.md
3. docs/01-foundation/domain/domain-model.md
4. docs/01-foundation/architecture/system-architecture.md
5. docs/90-cross-cutting/api-conventions.md
6. docs/90-cross-cutting/database-conventions.md
7. docs/90-cross-cutting/security.md

When working on a module, also read its local specification.

Rules:

- Do not bypass tenant isolation.
- Do not bypass permission checks.
- Follow existing modular boundaries.
- Do not introduce new dependencies without justification.
- Do not modify business rules without updating specification.
- Prefer existing platform capabilities over implementing duplicate functionality.
```

---

# 25. Documentation Rules

## Rule 1 — Business before implementation

Business specification không được phụ thuộc vào framework cụ thể nếu không cần thiết.

Không nên viết:

> Spring Controller gọi JpaRepository...

trong business specification.

---

## Rule 2 — One source of truth

Mỗi business rule chỉ nên có một nơi authoritative.

Các tài liệu khác link tới nó thay vì copy.

---

## Rule 3 — Không duplicate nghiệp vụ theo application

Business logic đặt ở module.

Admin Web / Teacher Web / Mobile chỉ mô tả cách expose nghiệp vụ.

---

## Rule 4 — Không block development vì tài liệu chưa hoàn thiện 100%

Module đạt `READY_FOR_DEV` là đủ để bắt đầu code.

---

## Rule 5 — Thay đổi business phải cập nhật specification

Nếu implementation khác specification:

- specification phải được cập nhật,
- hoặc implementation phải được sửa.

Không để hai nguồn mâu thuẫn lâu dài.

---

## Rule 6 — Architectural decision phải có ADR

Các quyết định quan trọng như:

- Modular Monolith
- Multi-tenancy strategy
- Authentication
- Event architecture
- Database
- Message queue

phải có ADR.

---

## Rule 7 — Foundation capability được tái sử dụng

Không tự tạo:

- notification engine,
- file storage,
- permission engine,
- workflow engine,

riêng cho từng module nếu đã có platform capability chung.

---

# 26. Naming Convention

Folder:

```text
lowercase-kebab-case
```

Ví dụ:

```text
academic-year
teaching-assignment
file-management
management-reporting
```

File:

```text
lowercase-kebab-case.md
```

Ví dụ:

```text
business-rules.md
data-model.md
acceptance-criteria.md
```

ADR:

```text
ADR-001-modular-monolith.md
ADR-002-multi-tenancy.md
```

---

# 27. Recommended Initial Implementation Order

## Foundation

```text
Domain Model
     ↓
Multi-tenancy
     ↓
Identity
     ↓
RBAC
     ↓
Audit
     ↓
File Management
     ↓
Notification
     ↓
Configuration
```

Một số capability có thể được triển khai song song tùy dependency.

---

## School Core

Khuyến nghị thứ tự:

```text
Academic Year
     ↓
Class
     ↓
Student
     ↓
Teacher
     ↓
Subject
     ↓
Teaching Assignment
     ↓
Timetable
     ↓
Attendance
     ↓
Grades
```

Đây là dependency-oriented order, không phải thứ tự bắt buộc tuyệt đối.

---

# 28. Kết luận

Documentation model của School Digital Platform dựa trên 5 nguyên tắc:

1. **Product-level docs giữ định hướng chung.**
2. **Foundation capability được quản lý xuyên suốt lifecycle.**
3. **Phase là milestone, không phải development lock.**
4. **Module là đơn vị specification và development.**
5. **Specification được hoàn thiện theo Progressive Specification.**

Cấu trúc logic tổng thể:

```text
Project Specification
        │
        ▼
      Phase
        │
        ▼
     Module
        │
        ▼
     Feature
        │
        ▼
Business Rule / Flow / API / Data
```

Mục tiêu cuối cùng:

> Cho phép hệ thống được phát triển nhanh theo MVP nhưng vẫn duy trì được kiến trúc, domain model và business specification đủ chặt chẽ để mở rộng thành một Digital School Platform lâu dài.
