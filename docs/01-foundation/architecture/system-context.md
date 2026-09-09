# System Context

Status: DRAFT

## Purpose

Describe who and what interacts with the School Digital Platform at a system boundary level.

## System under consideration

The School Digital Platform is a multi-tenant system for THPT schools. It provides shared foundation capabilities, School Core modules and later operational, digital and AI capabilities.

## Primary actors

| Actor | Main interaction |
|---|---|
| System Administrator | Platform-level tenant and operational administration |
| School Administrator | Administration within one school tenant |
| Ban Giám hiệu | School-wide monitoring, dashboards and reports |
| Tổ trưởng chuyên môn | Department-level monitoring and coordination |
| Giáo viên chủ nhiệm | Management of the assigned homeroom |
| Giáo viên bộ môn | Teaching, attendance and grading for assigned classes and subjects |
| Học sinh | Viewing personal academic information and school communication |
| Phụ huynh | Viewing information for linked children and receiving communication |
| Nhân viên nghiệp vụ | Business operations that are enabled for the role and phase |

## External systems and channels

- Admin Web.
- Teacher Web or Teacher Portal.
- Student App.
- Parent App.
- Email provider.
- Push notification provider.
- SMS or OTT adapter.
- Object storage.
- Excel and CSV exchange.
- SSO provider, when enabled.
- LMS, payment or other external platforms in later phases.
- Deployment, monitoring and backup services.

## System interactions

- Users authenticate and receive a tenant and authorization context.
- Web and mobile channels consume platform APIs.
- Business actions use shared tenant, permission, audit, file, notification and configuration capabilities.
- Import and export flows pass through validation, preview, confirmation and audit.
- External integrations are isolated behind integration contracts and operational logging.
- AI capabilities, when introduced, use authorized and auditable access to platform data.

## Out of scope for this document

- Specific frontend or backend frameworks.
- Specific database or hosting provider.
- Detailed endpoint contracts.
- Detailed deployment topology.
- Detailed external provider contracts.

## Open Questions

- Whether Student App and Parent App share one mobile application.
- Which external providers are required for the first pilot.
- Whether system administrators can access cross-tenant reporting and under what explicit authorization.
- What deployment environments and operational ownership are required beyond the stated DEV, UAT and PROD direction.

