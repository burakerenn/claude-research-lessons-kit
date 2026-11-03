# Research → Lessons Kit (for ChatGPT Projects)

The same method as the Claude Code kit in this repo, set up as a single ChatGPT Project. It turns evidence into **lessons that change decisions**, for technology, startup, business, engineering and AI work.

**research / your own results → lessons → decisions → outcomes → better lessons**

The assistant plays two roles: the research scout (RESEARCH) and the lessons keeper (LESSONS, REVIEW).

## Files
| File | Purpose | Where it goes |
|---|---|---|
| `project-instructions.md` | The assistant's working rules (7 commands) | Project → **Instructions** (paste everything below the line) |
| `lessons-learned.md` | The lessons file: Context, area table, field legend, ladders, 3 EXAMPLE lessons | Project → **Files** (upload) |
| `../retros/TEMPLATE.md`, `../decisions/TEMPLATE.md` | Optional: retro and decision forms you can fill in yourself | Keep them handy, or use RETRO / RECORD |

## Setup (5 minutes)
1. In ChatGPT, create a new **Project**.
2. Paste everything below the line in `project-instructions.md` into the project **Instructions**.
3. Fill in the **Context** section of `lessons-learned.md`. Add sub-topics you need; keep the seven areas.
4. Upload `lessons-learned.md` to the project **Files**.

## Commands
- **`RESEARCH <topic>`** (or `RESEARCH DEEP <topic>`): a report with graded claims, failures and base rates, what was not searched, and lesson candidates. Does not change the lessons.
- **`RETRO <what>`**: a short interview about something you did; ends with a RETRO block and ≤3 actions.
- **`LESSONS`**: turns the latest report, retro or outcome into lessons. Returns **only the changed entries** plus an integrity footer.
- **`FULL`**: returns the whole current file. Use it now and then to re-sync.
- **`GATE <decision>`**: pulls 1-3 lessons into the 7-line gate and gives you a Decision log row with a `uses:` marker.
- **`RECORD <decision>`**: drafts a decision record before the outcome; at review time, scores the process blind first, then the outcome.
- **`REVIEW`** (about monthly): stale, conflicting, unconfirmed and unused lessons; retirement by outcome. Changed entries + footer.

Without a command it chats normally and cites lesson IDs when relevant. Write in any language.

## Why only the changed entries?
When a model rewrites a whole file, it tends to drop or shorten entries without saying so, and you only notice weeks later. Returning just the changed lessons keeps the rest of your file untouched, and the integrity footer lets you check the arithmetic:
```
INTEGRITY · before: 12 · after: 13 · added: L-013 · retired/merged: – · changed: L-004 · check: 12 + 1 − 0 = 13
```
If the numbers do not add up, or `before` does not match your file, say "redo the footer against the uploaded file" before you paste anything.

## How to paste changes back
ChatGPT cannot edit a file you uploaded. After LESSONS or REVIEW:
1. Open your local `lessons-learned.md`.
2. For each **changed** ID, find its `### L-0xx` heading and replace that whole block with the new one.
3. Paste each **added** lesson under its area heading.
4. Move each **retired or merged** lesson to "Retired lessons", with the reason given.
5. Apply any Top 10 change and add the changelog line.
6. Count the `### L-` headings outside Retired lessons; it should equal `after`.
7. Delete the old file from the project Files and upload the new one.

If you skip the upload, the next chat sees the old lessons. Run `FULL` occasionally and compare its counts with your local file.

## First run
1. Fill in the Context and upload the file.
2. Do one `RESEARCH` on a question you care about, and one `RETRO` on something you did recently.
3. Run `LESSONS` after each. Check that every lesson has a cause and an action; push back if you get summaries.
4. Retire the 3 EXAMPLE lessons and upload the file again.
5. Before your next real decision, use `GATE`. When the outcome is known, run `LESSONS` on it.

## Limits
- Web search sometimes reads only a snippet. Snippet-only claims are grade F and enter at most as Open questions.
- Project Instructions have a length limit; the instructions stay under about 4,000 characters. Put extra rules in a project file.
- If the assistant drifts, say: "Redo this following the LESSONS rules in the instructions."
- Not tested on every ChatGPT plan.
