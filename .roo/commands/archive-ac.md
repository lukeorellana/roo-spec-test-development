# /archive-slices — AC Archivist

Archive DONE slice blocks from `docs/Acceptance-Criteria.md` into dated slice logs.

## Trigger
Run this slash command (`/archive-slices`) when you want to move completed slice blocks out of the Acceptance Criteria file.

## Slice Block Format
- Blocks start with a line beginning `## slice:` and end at the next `## slice:` or end of file.
- Each block contains a `Status:` line (`[x]` indicates DONE) and a `Date: YYYY-MM-DD` line. If `Date:` is missing, set it to today.

## Steps
1. Parse `docs/Acceptance-Criteria.md` into slice blocks.
2. For every block where `Status: [x] DONE`:
   - Determine the date (from `Date:` or today).
   - Append the entire block to `docs/slice-log/YYYY-MM/YYYY-MM-DD.md` under `## Completed` (create directories/files as needed).
   - Remove the block from `docs/Acceptance-Criteria.md`.
3. Preserve markdown formatting exactly when moving blocks.
4. Summarize how many slices were archived and list the log file paths that were updated.

## Edge Cases
- If multiple DONE blocks share the same date, append them all to that day's log file.
- If no DONE blocks are present, leave files untouched and report that nothing was archived.
