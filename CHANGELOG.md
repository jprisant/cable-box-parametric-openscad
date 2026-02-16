# Changelog

All notable changes to this project will be documented in this file.

## [Unreleased]

### Added
- Initial project scaffold with GitHub best-practice baseline files.
- Multi-LLM `AGENTS/` layout for `codex` and `claude-code`.
- CC BY-NC-SA 4.0 licensing documents and contribution terms.
- Docs skeleton (`FAQ`, `PRINTING`, `RELEASE`).
- Full parameter documentation in `docs/PARAMETER_REFERENCE.md`.
- Workflow guide in `docs/WORKFLOWS.md`.
- Folder scaffolding and contribution guides for `library/` and `community/`.
- OpenSCAD smoke automation templates promoted to first-class repo paths:
  - `.github/workflows/scad-smoke.yml`
  - `scripts/scad-smoke.ps1`
  - `scripts/scad-smoke.sh`
- Initial release artifact preset under `library/v1-default/`:
  - `stl/` baseline outputs
  - `images/` baseline previews
  - `config.json` and `notes.md`
- AGENTS tracking docs for current handoff:
  - updated `AGENTS/codex/INDEX.md`
  - updated `AGENTS/codex/TODO.md`
  - added current dated session-log entry in `AGENTS/codex/SESSION-LOG/`
  - added `AGENTS/codex/PLANNING/current-baseline-commit-plan.md`

### Changed
- Updated `cable-management-box-parametric.scad` header metadata with repo and SPDX license reference.
- Rewrote SCAD Customizer inline help for concise, parameter-level guidance.
- Removed numeric slider range annotations from user-facing Customizer parameters.
- Replaced `README.md` with accurate repository paths, docs map, and license references.
- Expanded `docs/FAQ.md` and `docs/PRINTING.md` to reflect current model behavior.
- Implemented true `Custom` placement behavior for front/back and left/right stabilizer alignment modes.
- Implemented true `Custom` behavior for bottom opening secondary alignment (centers within custom margin window).
- Tightened slicing validation (`Slice_Piece_To_Render` integer/range checks and clip parameter guards).
- Clarified opening offset directionality and legacy global offset behavior in SCAD inline help and docs.
- Deferred advanced experimental functionality from v1 release scope; working artifacts are retained under `AGENTS/codex/WORKING/`.
- Hardened local smoke scripts for real-world execution:
  - PowerShell runner uses deterministic process checks and parameter-set handling for `Part_To_Render`.
  - Bash runner supports `OPENSCAD_BIN` override and Windows Bash fallback executable paths.
