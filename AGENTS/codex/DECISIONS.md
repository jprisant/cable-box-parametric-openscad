# DECISIONS (codex)

## ADR-0001: Shared Multi-LLM Structure

- Date: 2026-02-12
- Status: accepted
- Decision: Use mirrored folder contracts for codex and claude-code under AGENTS/.
- Rationale: Reduces context drift and simplifies handoffs.
- Impact: Consistent workflows across agent tools.

## ADR-0002: v1 Scope Freeze Excludes Gridfinity

- Date: 2026-02-16
- Status: accepted
- Decision: Keep Gridfinity functionality out of `cable-management-box-parametric.scad` for v1 release.
- Rationale: User requested extra review time before including Gridfinity in first public release.
- Impact: Any Gridfinity-capable variants stay in `AGENTS/codex/WORKING/gridfinity/2026-02-13/` until explicitly promoted.

## ADR-0003: Maintain Advanced and Simplified Model Tracks

- Date: 2026-02-16
- Status: accepted
- Decision: Keep a simplified companion SCAD in `AGENTS/codex/WORKING/simplified/` while preserving the advanced core model as the release baseline.
- Rationale: Supports easier onboarding without collapsing advanced controls needed by power users.
- Impact: Promotion path for simplified variant is deferred to a post-v1 decision.
