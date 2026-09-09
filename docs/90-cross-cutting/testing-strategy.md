# Testing Strategy

Status: DRAFT

## Purpose

Define how product behavior, shared foundation controls and module specifications will be verified throughout progressive development.

## Scope

This is a test strategy, not a complete test plan. It verifies [Security Conventions](security.md), [API Conventions](api-conventions.md) and module behavior. Module acceptance criteria and test scenarios are created when each module becomes sufficiently specified.

## Test layers

### Domain and business rules

Verify core rules, state transitions, validation and calculations without depending on a delivery channel.

### Module integration

Verify a module with its persistence and shared capabilities, including tenant context, authorization, audit, file, notification or configuration behavior when relevant.

### API and channel contract

Verify request validation, response shape, authentication context, authorization failures, pagination, errors and integration compatibility.

### Security

Verify tenant isolation, role and scope evaluation, account lifecycle controls, secret handling, sensitive actions and file access.

### Import and export

Verify upload, validation, preview, error display, confirmation, import, export permissions and audit.

### End-to-end acceptance

Verify the approved happy-path flow for the module and the Phase 1 school cycle. Channels may be tested separately, but business outcomes remain owned by modules.

### Operational and resilience

Verify health checks, logging, monitoring, backup and restore procedures, integration retry behavior and long-running operation handling when those capabilities are available.

## Test data rules

- Test tenants must be isolated from one another.
- Test data must not contain real student or staff information unless an approved protected process exists.
- Fixtures should express the actor, tenant, role, scope and business state needed by the scenario.
- Tests for denied access are as important as happy-path tests.

## Specification gates

- DRAFT supports analysis and does not imply development readiness.
- READY_FOR_DESIGN means the business scope and domain are sufficiently clear for technical design.
- READY_FOR_DEV requires the Definition of Ready from the documentation structure.
- READY_FOR_TEST requires business rules and acceptance criteria sufficient for testing.
- DONE requires the specification to reflect the released behavior.

## Open Questions

- Which test tools and environments will be standardized?
- What minimum automated coverage is required for foundation capabilities?
- Which Phase 0 exit criteria must be tested in UAT?
- What performance, restore and availability thresholds apply to the pilot?
- How will test evidence be linked to specification and release status?
