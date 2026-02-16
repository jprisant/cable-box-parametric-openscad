# INDEX (codex)

## Pointers

- Context: `AGENTS/codex/CONTEXT.md`
- Tasks: `AGENTS/codex/TODO.md`
- Decisions: `AGENTS/codex/DECISIONS.md`
- Planning: `AGENTS/codex/PLANNING/`
- Session Logs: `AGENTS/codex/SESSION-LOG/`
- Transcripts: `AGENTS/codex/TRANSCRIPTS/`
- Working artifacts: `AGENTS/codex/WORKING/`

## Last Handoff

- Timestamp: 2026-02-16
- Completed in baseline (uncommitted working tree):
  - Core SCAD remains the v1 target and excludes Gridfinity functionality.
  - Gridfinity-capable artifacts are retained only in `AGENTS/codex/WORKING/gridfinity/2026-02-13/`.
  - Simplified companion model exists at `AGENTS/codex/WORKING/simplified/cable-management-box-parametric_simplified.scad`.
  - Opening-dimension validation was relaxed to allow odd sizing as long as dimensions are positive.
  - Documentation site scaffolding exists (`mkdocs.yml`, `docs/index.md`, `docs/*`) with docs workflow at `.github/workflows/docs-pages.yml`.
  - CI smoke scripts are in place under `scripts/` and workflow under `.github/workflows/scad-smoke.yml`.
- Current repository state:
  - `git status --short` shows an uncommitted baseline (`??` entries across repo paths).
  - v1 release is not yet pushed/tagged.
- Next session target:
  - Push v1 live.
- First actions next session:
  1. Validate OpenSCAD environment and run smoke scripts.
  2. Generate STL/PNG release artifacts and capture one physical validation result.
  3. Execute grouped commits from `AGENTS/codex/PLANNING/current-baseline-commit-plan.md`, push, and tag release.
- Continuation prompt:
  - "Run final validation + artifacts, then execute baseline commit plan and publish v1."
