# Invariants (Repo Defaults)

Use these defaults unless the repo says otherwise:

- Slice loop: AC → Plan (Files 1–2, Command 1, Artifact 1) → Tests-first → Minimal code → One command → Evidence
- One command: prefer `npm run quickcheck` (or a single chained command)
- Tests: prefer `node --test` / `pytest -q` depending on stack (docs-only slices may declare **no-test-needed**)
- Commit style: Conventional Commits
- **Canonical slice spec lives in `docs/Acceptance-Criteria.md` (AC-only)**
- New chat per slice (fresh session)
