# ADR 004: Custom Eval Harness

**Date:** 2025-11-01
**Status:** Accepted
**Deciders:** Jane Riveros

## Context
Need regression testing, red-teaming, and drift detection for multi-agent system. Existing platforms (LangSmith, W&B) are SaaS, expensive, and not tailored to regulatory gates.

## Decision
Build custom eval harness in Python (pytest-based) with domain-specific thresholds. Runs in CI (GitHub Actions) + nightly scheduled.

## Rationale
- Domain-specific thresholds (risk score drift, citation accuracy, compliance pass rate)
- Hard gates: blocks PR merge on regression failure
- Red-team prompts version-controlled alongside code
- No external dependency for core governance function
- Extensible for future formal verification

## Consequences
- Maintenance burden (accepted: solo-owned, well-tested)
- No managed dashboard (mitigated: GitHub Actions summary + custom Grafana panel)
- Must implement parallelization manually (pytest-xdist)