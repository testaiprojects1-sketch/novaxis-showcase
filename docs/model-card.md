# Novaxis OS / Atlas — Model Card

## Model Details
- **Model name:** Novaxis OS / Atlas (orchestration layer)
- **Version:** 1.0.0
- **Date:** November 2025
- **Owner:** Jane Riveros

## Intended Use
Multi-agent orchestration for regulated trading workflows: research, risk assessment, compliance checking. Designed for financial services firms requiring audit-ready AI decision pipelines.

## Limitations
- Not an order execution system (no OMS/EMS integration)
- Does not generate proprietary alpha
- Requires human review for final trade decisions
- Jurisdiction-specific compliance rules must be configured per deployment

## Evaluation Results
| Suite | Pass Rate | Threshold | Status |
|-------|-----------|-----------|--------|
| Regression | 97% | 95% | ✅ Pass |
| Red-team | 0 critical | 0 critical | ✅ Pass |
| Drift detection | <3% | <5% | ✅ Pass |
| Citation accuracy | 92% | 90% | ✅ Pass |

## Data Lineage
- Market data: Alpha Vantage, Polygon.io (licensed)
- News: NewsAPI, custom RSS feeds
- SEC filings: EDGAR public database
- Research corpus: Internal + public financial literature

## Governance
- Audit logging: Every decision traced via `trace_id`
- Eval harness: Runs on every PR + nightly
- Risk register: Reviewed quarterly
- Model card: Updated per release