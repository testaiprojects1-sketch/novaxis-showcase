# ADR 005: BPMN.js Integration for Visual Workflow Definition

**Date:** 2025-11-01
**Status:** Accepted
**Deciders:** Jane Riveros

## Context
Domain experts (compliance officers, risk managers) need to read and modify agent workflows. Code-only definitions create bottleneck.

## Decision
Integrate bpmn-js for visual BPMN 2.0 workflow definition. Workflows are executable (parsed to agent graph) and version-controlled as XML.

## Rationale
- BPMN is standard notation; compliance/risk teams already know it
- bpmn-js is mature, extensible, React-integrable
- XML is diffable, reviewable in PRs
- Executable: parser converts BPMN → agent graph at deploy time

## Consequences
- Added frontend complexity (bpmn-js bundle size)
- BPMN semantic gaps for AI agents (mitigated: custom extensions for LLM nodes, tool calls)
- Runtime execution engine needed (custom, lightweight)