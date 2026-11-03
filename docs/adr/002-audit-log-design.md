# ADR 002: Audit Log Design — Structured JSONL + Trace IDs

**Date:** 2025-11-01
**Status:** Accepted
**Deciders:** Jane Riveros

## Context
Regulated financial services require immutable, queryable audit trails for every AI decision. Must support SOX, SEC Rule 17a-4, Basel III.

## Decision
Structured JSONL audit logs with UUID v7 `trace_id` propagated through all services. OpenTelemetry-compatible spans. Dual write: Loki (hot, 30 days) + PostgreSQL (cold, 7 years) + S3 (raw payloads, 90 days).

## Rationale
- `trace_id` enables end-to-end correlation across agents, tools, LLMs
- JSONL is streaming-friendly, schema-evolvable, queryable in Loki/PostgreSQL
- OpenTelemetry compatibility allows future integration with standard observability stack
- Tiered storage balances cost vs. access patterns

## Consequences
- Storage volume significant (mitigated: compression, tiered retention)
- Schema evolution requires ADR process (enforced)
- Loki query language learning curve (documented)