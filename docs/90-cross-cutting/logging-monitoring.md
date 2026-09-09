# Logging and Monitoring Conventions

Status: DRAFT

## Purpose

Define shared observability expectations for application behavior, platform health, integrations and security-relevant operations.

## Scope

This document covers operational logs, metrics, health checks and correlation. It follows [API Conventions](api-conventions.md) and [Security Conventions](security.md). Audit is a separate authoritative concern for significant business and security actions.

## Observability signals

| Signal | Purpose |
|---|---|
| Application log | Explain an operational event or failure |
| Audit log | Record a significant actor action and affected data |
| Metric | Measure volume, latency, error rate, resource or business health |
| Health check | Report whether a service or dependency can perform its required role |
| Integration log | Record external exchange, mapping, retry and failure state |
| Correlation ID | Connect one request or operation across components |

## Structured event fields

Operational logs should include, where applicable:

- Timestamp.
- Severity.
- Event name.
- Correlation ID.
- Actor or system identity without secrets.
- Tenant context.
- Module or capability.
- Operation state.
- Safe error code.

Audit event fields follow the minimum in Security Conventions and must not be replaced by ordinary application logging.

## Redaction

Do not log passwords, session secrets, access tokens, private keys, unmasked sensitive data or unrestricted file contents. Error details must be safe for the audience and useful for internal diagnosis.

## Metrics and health

The platform should measure:

- API latency and error rate.
- Authentication and authorization failures.
- Tenant isolation violations or denied cross-tenant attempts.
- Import, export, report, notification and integration outcomes.
- Background operation duration and queue delay when applicable.
- Dependency and database health.

Health checks should distinguish the ability to accept traffic from the health of required dependencies.

## Alerting and retention

Alert thresholds, ownership, retention and escalation must be defined according to the first pilot's operational model. Operational logs and audit records have different access and retention policies.

## Open Questions

- Which logging and metrics backend will be used?
- What are the minimum latency, error-rate and availability alerts for the MVP?
- How long are application logs, integration logs and audit records retained?
- Who owns on-call response and operational review?
- Which security events require immediate alerts?
