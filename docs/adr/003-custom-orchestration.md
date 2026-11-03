# ADR 003: Custom Orchestration over LangGraph

**Date:** 2025-11-01
**Status:** Accepted
**Deciders:** Jane Riveros

## Context
Need multi-agent orchestration with: checkpointing, human-in-the-loop, governance hooks (audit, eval gates), deterministic routing.

## Decision
Build custom orchestration layer in TypeScript (Next.js API routes) rather than adopt LangGraph.

## Rationale
- Full control over checkpointing format, state serialization, governance injection points
- No framework abstraction leakage; audit logs are first-class, not afterthought
- Simpler mental model for solo developer; easier to debug
- LangGraph adds learning curve and vendor lock-in for marginal benefit at this scale

## Consequences
- More boilerplate (router, planner, state management)
- No built-in visualization (mitigated: bpmn-js for visual workflow definition)
- Must maintain eval harness integration manually (accepted)