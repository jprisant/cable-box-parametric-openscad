# TODO (codex)

## Next Session Target

Push v1 live from the current repository baseline.

## v1 Go-Live Checklist (Release Blockers)

- [ ] Confirm OpenSCAD CLI availability and record version (`openscad --version`).
- [ ] Run smoke validation scripts from repo root:
- [ ] `powershell -NoProfile -ExecutionPolicy Bypass -File scripts/scad-smoke.ps1`
- [ ] `bash scripts/scad-smoke.sh`
- [ ] Run direct compile checks on both models:
- [ ] `cable-management-box-parametric.scad`
- [ ] `AGENTS/codex/WORKING/simplified/cable-management-box-parametric_simplified.scad`
- [ ] Generate baseline release artifacts (at minimum default profile):
- [ ] STL output(s)
- [ ] PNG preview output(s)
- [ ] Store outputs under `library/` or `examples/` with clear names.
- [ ] Complete one physical validation print and capture fit/tolerance notes.
- [ ] Final documentation consistency pass (`README.md`, `CHANGELOG.md`, `docs/*`).
- [ ] Stage and commit with `AGENTS/codex/PLANNING/current-baseline-commit-plan.md`.
- [ ] Push branch and publish/tag v1.

## Completed Since 2026-02-13

- [x] Core v1 model excludes Gridfinity functionality.
- [x] Gridfinity artifacts retained in `AGENTS/codex/WORKING/gridfinity/2026-02-13/`.
- [x] Simplified variant created at `AGENTS/codex/WORKING/simplified/cable-management-box-parametric_simplified.scad`.
- [x] Opening validation relaxed to allow odd sizing (positive dimensions only).
- [x] MkDocs-style docs scaffold and docs workflow added (`mkdocs.yml`, `docs/`, `.github/workflows/docs-pages.yml`).

## Post-v1 Backlog

- [ ] Promote simplified variant into a supported public release path (final naming/versioning).
- [ ] Add at least 3 curated presets to `library/` (`.json + .stl + image`).
- [ ] Add first community example under `community/<handle>/<project>/`.
- [ ] Add repeatable STL+PNG render/export automation.
- [ ] Revisit Gridfinity as a separate post-v1 feature track.
