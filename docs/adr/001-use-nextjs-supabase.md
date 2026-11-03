# ADR 001: Use Next.js 15 + Supabase over Custom Python/FastAPI

**Date:** 2025-11-01
**Status:** Accepted
**Deciders:** Jane Riveros

## Context
Novaxis OS needed a full-stack platform for the web UI, API, authentication, realtime updates, and vector search. Options considered:
- Custom Python (FastAPI) + React + self-hosted PostgreSQL + pgvector
- Next.js 15 (App Router) + Supabase (PostgreSQL + Auth + Realtime + pgvector) + Vercel

## Decision
Choose Next.js 15 + Supabase + Vercel.

## Rationale
- Unified frontend/backend in TypeScript reduces context switching
- Supabase provides managed PostgreSQL, Auth, Realtime, pgvector, Edge Functions
- Vercel offers zero-config deploy, preview deployments, edge caching
- Faster iteration for solo founder; lower operational burden
- TypeScript end-to-end improves refactoring safety

## Consequences
- Less control over Python ML stack (mitigated: Python services via Supabase Edge Functions or separate containers)
- Vendor lock-in to Supabase/Vercel (accepted: portable PostgreSQL schema)
- Team must be proficient in TypeScript/React (met)