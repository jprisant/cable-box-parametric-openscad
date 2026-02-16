# AGENTS Collaboration Standard

This directory defines a multi-LLM operating model for this repository.

## Goals

- Keep project truth in tracked source/docs.
- Keep agent-specific context organized and minimal.
- Make handoffs deterministic across agents.

## Directory Contract

- `AGENTS/index.md` - Top-level map and latest handoff pointers.
- `AGENTS/codex/` - Codex-specific context and logs.
- `AGENTS/claude-code/` - Claude Code-specific context and logs.

Each agent folder contains:

- `CONTEXT.md` - Current state and constraints.
- `TODO.md` - Active tasks and next actions.
- `DECISIONS.md` - ADR-lite decision records.
- `INDEX.md` - Quick index to current artifacts.
- `SESSION-LOG/` - Session summaries.
- `PLANNING/` - Plans and analysis docs.
- `TRANSCRIPTS/` - Raw or curated transcript copies.

## Cross-Agent Rules

1. Update canonical docs first (`README.md`, `docs/`, source files).
2. Record only durable decisions in `DECISIONS.md`.
3. Keep `CONTEXT.md` short and current.
4. End each working session with:
- TODO update,
- decision update (if applicable),
- session log entry,
- handoff note in `INDEX.md`.
5. Do not reference `_NOTES/` from public-facing docs.

## Conflict Avoidance

- One agent per branch when possible.
- If two agents touch same file, merge by explicit review.
- Treat `AGENTS/*` as coordination support, not source of product truth.
