# Product Principles

Status: DRAFT

## Purpose

Capture the product and architecture principles that should guide future specifications and prevent customer-specific or implementation-led drift.

## Principles

### Product Core first

Capabilities common to most THPT schools belong in the reusable core.

### Configuration first

Differences between schools should be represented through configuration where practical, including academic periods, grading rules, permissions, workflows, notifications, forms and enabled modules.

### Modular Monolith baseline

The MVP uses a modular monolith direction. Modules have clear business boundaries while remaining part of one initial system. Microservices require a separate justified decision.

### Multi-tenant by design

Each school is treated as a tenant. Core business data must be isolated by tenant, and configuration may vary by tenant.

### API first

Important capabilities expose stable APIs for Admin Web, Teacher Web, Student App, Parent App and future integrations.

### Audit by default

Sensitive actions, especially access, imports, permission changes, student data changes and grade changes, must be traceable. The minimum audit event fields are defined in [Security Conventions](../90-cross-cutting/security.md).

### Business before implementation

Business specifications describe actors, scope, rules, flows and outcomes. Frameworks, repositories and UI components belong in technical design documents when they are needed.

### Progressive specification

Documentation becomes more detailed as decisions mature. A small useful specification is preferred over a complete tree of empty or speculative files.

### One source of truth

Each business concept and rule has one authoritative document. References and links are preferred to duplicate copies.

### Reuse shared capabilities

Permission, audit, notification, configuration, file management and later workflow capabilities are platform capabilities, not separate implementations inside every business module.

## Open Questions

- Which technical choices require an ADR before the first implementation?
- What minimum configuration surface is required for the first pilot?
- Which pilot-specific variations should remain configuration rather than become new modules?
