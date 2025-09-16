# Roo Spec Test Driven Development

## Purpose
Demonstrates a spec-first workflow for AI-assisted coding using the Roo Orchestrator.

## Spec-Based AI Coding vs Vibe Coding
Spec-Based AI Coding uses explicit Acceptance Criteria, a tiny plan, tests first, and one-command evidence so each commit is deliberate and reproducible.
Vibe Coding lets the model "wing it" without a contract or tests, leading to unpredictable and harder-to-review changes.

## Quick Start
Paste this prompt into Roo task to bootstrap your project:

```
System objective: Bootstrap this repo with the Roo Orchestrator Framework.

Do the following atomically:
1) Detect OS (macOS/Linux or Windows PowerShell).
2) Ask: "Which programming language does this project use?"
   - Purpose: to update `.roo/rules-code/00-invariants.md` with language-specific commands and test tools.
   - If the user asks why, reply: "This sets rule invariants so the agent follows standards for your language."
3) In a temp directory, run:
   git clone https://github.com/lukeorellana/roo-spec-test-development <temp>
4) Copy into the current repo root:
   - <temp>/.roomodes                       → .roomodes   (overwrite)
   - <temp>/.roo/rules-code/**                → .roo/rules-code/ (merge/overwrite)
5) Update `.roo/rules-code/00-invariants.md` with defaults for the chosen language
   (e.g., Node: `npm run quickcheck` + `node --test`; Python: `pytest`; etc.)
6) Print a short “Bootstrap OK” report listing created/updated paths.
7) Do NOT modify any other files.

Acceptance checks (must pass):
- `.roomodes` present in repo root and contains the custom modes.
- `.roo/commands/` exists and includes the slash commands (e.g., init/handoff/result/return).
- `.roo/rules-code/00-invariants.md` reflects the selected language.
- Final console output shows each path written.

If shell access is unavailable, tell me exactly which commands to run for my OS instead of proceeding.

```

## Slice-First (AC-only) Loop

1) New chat → **📝 Slice Spec Writer**  
   “Goal: <small thing>. **Activate** this slice. Command: `<one command>`.”  
   → It appends a slice block to `docs/Acceptance-Criteria.md` and marks it `[>] ACTIVE`.

2) Switch to **Code**  
   Code mode selects the ACTIVE block → **tests-first** → minimal change → **one command** → paste **trimmed logs** into the slice’s **Evidence** → set `Status: [x] DONE`.

3) **Archive**
   Run **🗃️ AC Archivist** with the `/archive-slices` slash command.
   → DONE blocks move to `docs/slice-log/YYYY-MM/YYYY-MM-DD.md`.

4) Repeat (one new chat per slice).

> Invariants: quick command (`npm run quickcheck`), tests-first, conventional commits. See `.roo/rules-code/00-invariants.md`.
