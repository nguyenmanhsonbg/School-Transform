# ADR-001: Modular Monolith Baseline

Status: Proposed

## Purpose

Record the initial architecture baseline and the conditions under which it should be reconsidered.

## Context

The product must support multiple foundation capabilities, School Core modules and later phases. The first release is an MVP that needs clear boundaries and fast iteration, while avoiding premature distributed-system complexity.

## Decision

Use a Modular Monolith as the baseline architecture for the MVP and the initial School Core releases.

The system remains one deployable product boundary at the beginning, with explicit foundation and business module boundaries. Module ownership, dependency rules and contracts are documented even when the modules share the initial runtime and persistence environment.

## Affected documentation

- [System Architecture](../01-foundation/architecture/system-architecture.md)
- [Modular Architecture](../01-foundation/architecture/modular-architecture.md)
- [Product Principles](../00-product/product-principles.md)

## Alternatives considered

- Microservices from the first release.
- A single undifferentiated application without module boundaries.
- A separate deployment for every Phase.

## Rationale

- It matches the explicit roadmap baseline.
- It supports end-to-end delivery with a small initial team.
- It keeps tenant, identity, RBAC, audit and business modules within a consistent security boundary.
- It preserves a path to extract a module later when scale, ownership or operational evidence justifies it.

## Consequences

### Positive

- Lower operational complexity for the MVP.
- Faster cross-module iteration during domain discovery.
- Clear module boundaries can be established before service extraction.

### Trade-offs

- The team must actively prevent private data access and hidden coupling between modules.
- Shared deployment and persistence can make module independence weaker if contracts are not maintained.
- Extraction later may require deliberate migration of data and operational responsibilities.

## Revisit criteria

Reconsider this decision only when demonstrated scale, independent deployment needs, team ownership, compliance, fault isolation or another material requirement cannot be met safely by the modular monolith.

## Open Questions

- Which module contract mechanism will be used?
- What deployment and persistence choices best preserve the boundaries?
