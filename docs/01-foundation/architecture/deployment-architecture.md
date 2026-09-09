# Deployment Architecture

Status: DRAFT

## Purpose

Define the initial deployment direction and operational environments required to support the Modular Monolith roadmap.

## Scope

This document defines deployment goals and boundaries for the [System Architecture](system-architecture.md). It follows [Security Conventions](../../90-cross-cutting/security.md). It does not select a cloud vendor, container platform, database engine or CI/CD product.

## Environment direction

The roadmap identifies:

- DEV for active development.
- UAT for integration and pilot validation.
- PROD for released school operations.

Configuration, credentials, data and access must be separated by environment.

## Baseline deployment shape

The Modular Monolith is the initial application deployment unit. It may depend on separately managed services for database, file storage, notification adapters, external integrations, monitoring and backup.

The deployment shape must preserve the documented tenant, identity, RBAC, audit, security and module boundaries.

## Delivery and operations

The first operational baseline requires:

- A CI/CD pipeline.
- A deployable UAT environment.
- Versioned database migrations.
- Health checks.
- Application and integration logging.
- Basic monitoring.
- Database backup and restore testing.
- Controlled configuration and secret management.

## Reliability direction

The initial roadmap target is 99.5 percent availability, with ordinary APIs targeted below two seconds under standard load. Large imports and reports should not block the primary request when background processing is needed.

These targets require validation against the first pilot workload before being treated as an SLA.

## Deployment safety

- Releases must be traceable to a version and environment.
- Schema changes must be compatible with the rollout sequence.
- Health checks and rollback behavior must be defined before production use.
- Tenant data must remain isolated during migration, backup and restore.
- Operational access must be role-controlled and auditable.

## Open Questions

- Which hosting and runtime platform will be used?
- How is the Modular Monolith packaged and scaled?
- Which database, file storage and notification services are selected?
- What rollback and zero-downtime requirements apply?
- What backup retention, recovery point and recovery time objectives are required?
- What availability and performance targets will the pilot formally accept?
