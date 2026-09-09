# System Architecture

Status: DRAFT

## Purpose

Define the implementation-neutral system architecture direction for the MVP and provide guardrails for later technical design.

## Baseline

The initial architecture is a Modular Monolith. Foundation capabilities and business modules remain clearly separated inside one system boundary and can be evolved independently without prematurely introducing distributed deployment complexity.

## Logical areas

### Product and domain layer

Contains product concepts, domain models, module ownership and business rules.

### Application capability layer

Coordinates use cases, authorization checks, tenant context, validation, transactions and calls to shared capabilities or other module contracts.

### Interface layer

Provides versioned APIs and channel-specific interfaces for Admin Web, Teacher Web, Student App, Parent App and integrations.

### Infrastructure layer

Provides persistence, file storage, notification adapters, external integrations, deployment and operational services. Technology choices remain outside this baseline document.

## Shared platform concerns

Every request that accesses tenant business data must carry a valid tenant context and authorization context. Sensitive actions must be auditable. Common validation, error handling, correlation and observability conventions apply across modules.

## Data and control flow

1. A channel or integration submits a request through a versioned interface.
2. The system establishes identity and tenant context.
3. RBAC evaluates permission and scope.
4. The owning module validates and executes its business rule.
5. Shared audit, notification, file or configuration capabilities are used where applicable.
6. The result is returned through the channel contract and operational signals are recorded.

## Quality direction

The roadmap calls for tenant isolation, versioned APIs, consistent errors and validation, logging, correlation ID, database migration, health checks, backup, basic monitoring, DEV/UAT/PROD environments and CI/CD. Detailed targets and technical mechanisms belong in cross-cutting documents and ADRs.

## Constraints

- Do not assume microservices, event sourcing, CQRS, Kafka or Kubernetes for the MVP.
- Do not make a business specification depend on a framework.
- Do not bypass tenant isolation, authorization or audit for convenience.
- Do not allow a channel to own a business rule that belongs to a module.

## Open Questions

- Which application and infrastructure technologies will be selected?
- What persistence model and transaction boundaries are required?
- Which operations need background processing?
- What is the minimum deployment, backup and monitoring topology for the first pilot?

