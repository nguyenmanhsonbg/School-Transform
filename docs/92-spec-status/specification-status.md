# Specification Status

Status: DRAFT

## Purpose

Track the maturity of the documentation set so Product, BA, Design, Development and Testing can work in parallel without treating file existence as development readiness.

## Status vocabulary

| Status | Meaning |
|---|---|
| DRAFT | The specification is being analyzed or refined |
| READY_FOR_DESIGN | Business scope and domain are sufficiently clear for technical design |
| READY_FOR_DEV | The Definition of Ready for Development is satisfied |
| IN_DEVELOPMENT | Implementation is in progress and specification refinement may continue |
| READY_FOR_TEST | Business rules and acceptance criteria are sufficient for testing |
| DONE | Released behavior is reflected by the specification |

## Current specifications

All specifications created through Batch 2 remain DRAFT. They establish direction and identify open decisions; none is READY_FOR_DEV solely because the file exists.

### Product

| Document | Status | Notes |
|---|---|---|
| docs/00-product/product-vision.md | DRAFT | Product direction |
| docs/00-product/product-scope.md | DRAFT | Product and phase boundary |
| docs/00-product/product-principles.md | DRAFT | Product guardrails |
| docs/00-product/glossary.md | DRAFT | Terminology and naming decisions |
| docs/00-product/roadmap.md | DRAFT | Phase dependencies and exit criteria |

### Foundation: domain and architecture

| Document | Status | Notes |
|---|---|---|
| docs/01-foundation/domain/domain-overview.md | DRAFT | Domain landscape |
| docs/01-foundation/domain/domain-model.md | DRAFT | Conceptual entities and relationships |
| docs/01-foundation/domain/domain-boundaries.md | DRAFT | Ownership boundaries |
| docs/01-foundation/architecture/system-context.md | DRAFT | Actors and external systems |
| docs/01-foundation/architecture/system-architecture.md | DRAFT | System direction |
| docs/01-foundation/architecture/modular-architecture.md | DRAFT | Module and dependency guardrails |
| docs/01-foundation/architecture/deployment-architecture.md | DRAFT | Environment and deployment direction |

### Foundation: tenant, identity and access

| Document | Status | Notes |
|---|---|---|
| docs/01-foundation/multi-tenancy/specification.md | DRAFT | Tenant meaning and baseline rules |
| docs/01-foundation/multi-tenancy/tenant-isolation.md | DRAFT | Isolation scenarios and enforcement direction |
| docs/01-foundation/multi-tenancy/data-strategy.md | DRAFT | Data classification and physical strategy options |
| docs/01-foundation/identity/specification.md | DRAFT | Identity capability baseline |
| docs/01-foundation/identity/authentication.md | DRAFT | Authentication behavior |
| docs/01-foundation/identity/account-lifecycle.md | DRAFT | Account states and transitions |
| docs/01-foundation/rbac/specification.md | DRAFT | RBAC capability baseline |
| docs/01-foundation/rbac/permission-model.md | DRAFT | Permission tuple and evaluation direction |

### Cross-cutting

| Document | Status | Notes |
|---|---|---|
| docs/90-cross-cutting/api-conventions.md | DRAFT | API rules |
| docs/90-cross-cutting/database-conventions.md | DRAFT | Persistence rules |
| docs/90-cross-cutting/security.md | DRAFT | Shared security rules |
| docs/90-cross-cutting/error-handling.md | DRAFT | Error classification and handling |
| docs/90-cross-cutting/logging-monitoring.md | DRAFT | Operational observability |
| docs/90-cross-cutting/testing-strategy.md | DRAFT | Verification strategy |
| docs/90-cross-cutting/integration-principles.md | DRAFT | External system boundaries |

## Architectural decisions

| ADR | Status | Notes |
|---|---|---|
| docs/91-decisions/ADR-001-modular-monolith.md | Proposed | MVP architecture baseline |
| docs/91-decisions/ADR-002-multi-tenancy.md | Proposed | Initial tenant boundary |

Authentication, database technology, deployment provider and the complete permission matrix remain open decisions and are not represented as accepted ADRs.

## Definition of Ready for Development

Before a module or capability can move to READY_FOR_DEV, it must have:

- Purpose.
- Scope.
- Actors.
- Core use cases.
- Critical business rules.
- Main entities.
- Permission model.
- Happy-path user flow.
- Main dependencies.

Complete API detail, every error case, every UI detail, every test case and every edge case may be refined in parallel after the minimum is satisfied.

## Scope boundary

Phase 1 module specifications are intentionally not created or assigned a status in Batch 2. They will be added progressively after the foundation decisions and naming questions are reviewed.

## Open Questions

- Who owns status changes and who approves READY_FOR_DEV?
- How will evidence for each status be linked to a specification?
- Should status tracking include implementation and test evidence in the same table?
- When should a Proposed ADR become Accepted?

