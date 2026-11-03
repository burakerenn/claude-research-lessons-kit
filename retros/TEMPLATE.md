# Retro: protocol and template

Run a retro after each finished job, at a decision's review date, and after an incident. About 15 minutes. Save it as `retros/R-YYYY-MM-DD-<slug>.md` only when it holds a "learn" action; otherwise the RETRO block in your log is enough.

## Interviewer rules
- The interviewer did not do the job (another agent, a fresh session, or a teammate).
- No praise, no verdicts. Say "the job", never "you".
- One challenge per retro. Agreement after pushback is not evidence.
- Work from records (log, commits, reports, transcripts), not memory.

## Protocol
1. **Open actions first:** read the open items in `retros/ACTIONS.md` for this area.
2. **Timeline:** confirm what happened from the records, in order, with dates and numbers.
3. **The gap:** planned vs happened · what was known at the time · where we got lucky · has this happened before · what still went wrong inside a success.
4. **Lessons:** which IDs were used, skipped, or found wrong, and why.
5. **≤3 actions**, each tagged **fix-now** (do it, it is a task) or **learn** (goes to the keeper as own-outcome evidence), with owner, end state and due date. Big system changes wait ~2 days before they are made.
6. **Read back** the block to the job owner, for factual corrections only.

## RETRO block
```
RETRO · <job> · <date> · interviewer: <who>
Planned: … · Happened: … · Gap: …
Lucky: … · Recurrence: yes (LA-/L-ID) / no
Lessons: used L-… · skipped L-… (why) · wrong L-… (why)
Actions: LA-0xx fix-now <owner> <end state> <due> · LA-0yy learn …
Parked: …
```
Fix-now actions go to your task list and `retros/ACTIONS.md`. Learn actions go to the next keeper run.

## Action fields (`retros/ACTIONS.md`, one line per action)
`LA-ID · Lesson · Action · Rung · Type (fix-now/learn) · Owner · Priority P0/P1/P2 · Due (P0 1 week, P1 4 weeks, P2 next quarter) · Status (open → implemented → verified / dropped) · Evidence · Verified on · Recurrence · Next review`

## Questions that help in step 3
- What did success look like before we started (numbers if possible)?
- What failed, and what is the root cause? Ask "why?" until you reach something you control.
- What surprised us? What early warning sign, in hindsight, showed the problem?
- Did the lessons we relied on hold: held / partly / did not hold?
