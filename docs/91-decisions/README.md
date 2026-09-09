# Architecture Decision Records

Status: DRAFT

## Purpose

Maintain the decisions that materially affect product architecture, module boundaries, data isolation or long-term evolution.

## ADR rules

- Record the context, decision, alternatives, rationale, consequences and status.
- Create an ADR only for a real architectural decision.
- Keep unresolved implementation details as Proposed / To Be Confirmed or Open Question.
- Link affected specifications and update them when a decision changes.
- Do not use ADRs to duplicate business rules already owned by a module.

## Current decisions

- [ADR-001 — Modular Monolith baseline](ADR-001-modular-monolith.md).
- [ADR-002 — Multi-tenancy boundary](ADR-002-multi-tenancy.md).

Authentication provider, database technology, deployment topology and other unconfirmed choices do not receive an accepted ADR until the decision is sufficiently defined.

## Open Questions

- Who approves Proposed and Accepted ADR statuses?
- Should ADR review be tied to a release or to the affected specification batch?
