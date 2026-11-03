# Claude Research → Lessons Kit

Claude Code subagents and templates that turn evidence into **lessons that change decisions**, for technology, startup, business, engineering and AI work (plus legal, security, risk, team and operations).

**research / your own results → lessons → decisions → outcomes → better lessons**

Most of what we learn gets lost. A report ends as a summary, a failed project ends as a bad memory, and the same mistake comes back six months later. This kit keeps a small, living set of lessons. Each says what happened, why, and what to do differently, with graded evidence and a status. Lessons are pulled in at the moment of a decision, their use is marked, and the outcome flows back to correct them.

It comes from a working multi-agent setup, cut down to the parts that make the loop work for one person or a small team.

## The loop
1. **Research.** `research-scout` searches the web (a quick check or a deep report), grades every claim, logs its searches and what it did not search, and writes a dated report. It never writes lessons.
2. **Retro.** After a job, an incident or a decision's review date, someone who did not do the job runs a short retro from the records.
3. **Lessons.** `lessons-keeper` gates what enters, edits one lesson at a time, moves lessons up a status ladder and returns a change list.
4. **Decide.** Before a decision that matters, pull 1-3 lessons into a 7-line gate and mark the decision `uses: L-xxx`. Big decisions get a record, written before the outcome.
5. **Close the loop.** At the review date, score the process blind, then add the outcome. The result goes back to the keeper.

## Why it works this way (in plain words)
- **Learned means changed and checked.** A lesson counts once something changed (a checklist, a prompt, a tool, a rule) and a later case showed it worked. Until then it is a note. The status ladder (watch → identified → actioned → embedded → verified) makes this visible, and the rung ladder (R0 reference … R5 tool removed) says how strongly it is built in.
- **Pull 1-3 lessons at the decision.** Lessons read "in general" change little. A few lessons, quoted at the moment of choice with "honoured" or "skipped because", change more than many lessons loaded everywhere. "No lesson applies" is a fine answer.
- **Keep the always-read part small.** One file at first; later a short index plus one file per area. You read the index and open only the files your decision needs.
- **Edit, don't regenerate.** Asking a model to rewrite the whole lessons file loses entries quietly. The keeper edits one lesson per change, and in ChatGPT the assistant returns only the changed entries plus a count check.
- **The keeper is the poisoning target.** Web text flows into reports, reports flow into lessons, and lessons are read as trusted for months. The realistic attack is a quiet vendor preference or a false number, not "ignore all instructions". So: source text stays in blockquotes, the keeper never lifts an Action from a quote, thin evidence enters only as `watch`, and a shape check looks for instruction-like words and hidden characters.
- **Measure use, not volume.** The number of lessons or reports is not progress. What matters: how often decisions carry a `uses:` marker, how often a lesson was pivotal, how many lessons are built in at R3 or higher, and whether failures come back.
- **The system must give more time than it takes.** Small budgets, and a ritual skipped twice gets shrunk, not patched with more tooling.

## What's inside
| Path | What it is |
|---|---|
| `.claude/agents/research-scout.md` | Web researcher: quick/deep levels, 12-step method, source × claim grades, likelihood words, search log, "not searched", source quotes only in blockquotes |
| `.claude/agents/lessons-keeper.md` | The only writer of the lessons: admission gate, one lesson per edit, status and rung ladders, contradictions, retirement by outcome, shape check, review mode, change-list return |
| `.claude/agents/claim-checker.md` | Optional, read-only: truth gate on new lessons, blind process scoring of decisions, harness grading |
| `CLAUDE.md` | The flow in a few lines plus the 7-line decision gate (copy into your own CLAUDE.md) |
| `research/lessons-learned.md` | Single-file starter: Context, the 7-area table, field legend, ladders, Top 10, 3 EXAMPLE lessons |
| `research/lessons/INDEX.md` | Index template for when you split: how to use, Top 10, one line per lesson |
| `research/lessons/area-example.md` | An area file with 2 EXAMPLE lessons |
| `research/report-template.md` | Deep report template |
| `decisions/TEMPLATE.md` | 7-line gate, decision record, two-part review, one EXAMPLE |
| `retros/TEMPLATE.md` | Retro protocol, interviewer rules, RETRO block, action fields |
| `chatgpt/` | The same method as one ChatGPT Project |

## Quick start (Claude Code)
1. Copy `.claude/agents/`, `CLAUDE.md`, `research/`, `decisions/` and `retros/` into your project root. If you already have a CLAUDE.md, paste this one's content into it.
2. Fill in the **Context** section of `research/lessons-learned.md`: who you are, what you build, stage, stack, constraints, upcoming decisions. Every lesson is applied to it.
3. Skim the area table; add sub-topics you need, keep the seven areas.
4. Restart Claude Code (or open `/agents`) so the agents load.
5. Delete `research/lessons/` until you need it (see "When to split").

## Usage
Ask in the main session:
- *"Quick check: what does the cheapest managed Postgres cost at 50 GB?"* → `research-scout`, quick level.
- *"Deep research: how B2B AI tools price heavy users, and which ones failed."* → a deep report in `research/YYYY-MM-DD-<slug>.md` and a short summary.
- *"Retro on last month's launch."* → the retro protocol; ≤3 actions.
- *"Turn that report into lessons."* → `lessons-keeper` returns a change list (`L-007 ADD: research/… §3`) and the top 3 to act on.
- *"Should we launch with a free tier or a trial? Gate it."* → 1-3 lessons, the 7-line gate, a `uses:` marker.
- *"Review the lessons."* (monthly) → review mode; commit first, then read the diff.

Retire the EXAMPLE lessons after your first real keeper run.

## Rituals and budget
| Ritual | When | Cap |
|---|---|---|
| Gate | Each decision that matters | 7 lines, ~5 min |
| Retro | Each finished job, review date or incident | ~15 min, ≤3 actions |
| Weekly check | Fixed weekday | 10 min: batch uncurated reports into one keeper run; open actions; reviews due |
| Monthly | First week | One review-mode run, one claim-check sample, one row of numbers |
| Quarterly | Every 3 months | 30 min: did our own rules cause repeated problems? Optional harness re-run |

Keep the loop to roughly a tenth of your agent runs. If you must cut, drop in this order: harness re-runs, forecast practice, usage numbers, the weekly check (fold it into monthly). Keep the gate (lessons line and decider line), records for big decisions, and edit-don't-regenerate.

## When to split
Start with one file. When `research/lessons-learned.md` passes about **150 lines of lessons or 16,000 characters**, move to `research/lessons/`: an `INDEX.md` (always read first; ≤150 lines, ≤15,000 characters) and one file per area (≤16,000 characters each), plus `retired.md`, `open-questions.md` and `changelog.md`. IDs never change. The old file becomes a short stub pointing to the index. Split an area file by sub-topic when it passes its cap.

## What to measure
Monthly, once you have 2-3 months of baseline: share of gates with a `uses:` marker (incl. "none"); share of decisions where a lesson was pivotal; share of embedded lessons at R3+; actions closed by their due date; failures that came back while a lesson existed; median days from identified to embedded; forecast Brier score with its sample size. Not the number of lessons.

## Evaluation harness (optional smoke test)
To check that lessons actually improve decisions, write **20 short decision questions** as they stood at the time: about 12 where a lesson should apply, about 5 where none should (over-application check), and about 3 that rest on an expired fact. Keep an answer key apart, and never let the keeper read it. Run each question **with** lessons (index + up to 3 area files) and **without** (Context only), twice each. Have someone else grade blind: answers stripped of lesson IDs and mode, shuffled, scored 0-8 (right action, caveat present, no over-application, honest uncertainty), after agreeing on a few hand-graded calibration cases. Compare paired scores per question. With 20 questions this only detects large effects: a null result means "no large effect", not "no effect". Add 5-8 fresh questions each quarter, dated after the lessons they test.

## Optional hardening
Prompts are speed bumps, not walls. If you rely on the loop, consider Claude Code hooks for the few rules that matter:
- Make the lessons folder (or file) writable only by the keeper agent, and block shell commands that write to it, so no other agent or script can slip a lesson in.
- Let the scout write only new, today-dated report files, and block every other agent from web access, so untrusted text has one narrow entry point.
- Run a read-only shape check before committing lesson changes (instruction-like words, URLs in Action lines, invisible characters, missing fields, more than five new lessons in one run); a hit stops the commit for a human look.
- Make hooks fail closed: if a check errors or cannot parse its input, it blocks rather than allows. Prefer block or allow over "ask" prompts, which get approved out of habit.
- Commit once per keeper run with the change list as the message, and snapshot before review mode, so any run can be rolled back.
- Pick models to fit your budget: the scout runs fine on a mid-size model; the keeper benefits from a stronger one.

## ChatGPT
`chatgpt/` holds the same method as one ChatGPT Project. Because ChatGPT cannot edit project files, the assistant returns only changed lessons plus an integrity footer, and you paste them back. See `chatgpt/README.md`.

## License
[CC BY 4.0](LICENSE): use, adapt and share, including commercially, with attribution.
