# Preflight Gate — AC-only (single-file)

You are the Code mode working in this repository. Before changing files, enforce these checks.
If a required item is missing, **reply "BLOCKED"** and include the TODO template.

## 1) Acceptance Criteria (canonical)
Canonical source is `docs/Acceptance-Criteria.md` consisting of **slice blocks**:

Required block shape:
- Heading: `## slice: <kebab-or-title>`
- Lines: `Status: [ ] TODO` (or `[>] ACTIVE` / `[~] IN-PROGRESS` / `[x] DONE`) and `Date: YYYY-MM-DD`
- Sections:
  - `### Acceptance Criteria` (3–8 bullets; unchecked)
  - `### Plan` with exactly three lines:
    - `- Files: <file1>, <file2>`
    - `- Command: <one command>`
    - `- Artifact: <one result>`

### Target slice resolution (in order)
1) If any block has `Status: [>] ACTIVE` → use the first such block.
2) Else use the first block with `Status: [ ] TODO`.
3) Else, if the user names a slice by slug/title in chat, use that block.
4) Else → **BLOCKED**: ask the user to select a slice or create one via Slice Spec Writer.

### Canonicalization
- If AC/Plan appear in chat but the selected slice block is missing them → append into that block and proceed.
- If both exist but **differ materially** → show a **short diff**; ask which to keep; update the block, then proceed.
- If no AC anywhere → **BLOCKED** and print the slice template (below).

## 2) Small Plan (3 lines, mandatory)
- Files: name 1–2 paths only
- Command: a single command (e.g., `npm run quickcheck`, `pytest -q`)
- Artifact: one file/result

## 3) Tests First
- If touching `src/` or `tools/`, add/update tests **before** code (docs-only may declare **no-test-needed**).

## 4) Evidence
- Run the single command; show **trimmed logs** (summarize errors). If red → fix or stop.

## When all checks pass
1. Summarize the plan in **≤5 lines**.
2. Add/adjust tests **first**.
3. Make the **smallest** code change to satisfy AC.
4. Run the command and show trimmed logs.
5. Stop and wait for review (or commit to trunk if solo).

## TODO template (when BLOCKED)

## slice: <kebab-or-title>
Status: [ ] TODO
Date: YYYY-MM-DD

### Acceptance Criteria
- [ ] Bullet 1
- [ ] Bullet 2
- [ ] Bullet 3

### Plan
- Files: <file1>, <file2>
- Command: <one command>
- Artifact: <result>

### Evidence
