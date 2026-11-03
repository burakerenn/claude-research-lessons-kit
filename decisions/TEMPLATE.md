# Decisions: gate and record

Two sizes. Every decision that matters gets the **gate** (7 lines, ~5 minutes). Big ones also get a **record** file.

## The gate
Use it for: any spend; anything outward (send, publish, push to a public repo, sign); a project milestone; a new agent, tool, connector or scheduled job; anything hard to undo.
```
GATE · <decision in one line> · reversible: yes / partly / no
1 Decision and reversibility: <one line; what undoing it costs>
2 Lessons (1-3; max 5 incl. skipped): L-0xx "<Action line>" honoured how · L-0yy skipped because … | uses: none (why)
3 Pass / kill line: <observable state> by <date>
4 Premortem (costly or outward only): <most likely failure> → <mitigation>
5 Key claim: <claim> · grade <B2> · checked against source: yes/no   (money, legal, security: must be yes)
6 Decider: "<their own words>" · where recorded
7 Expect: <outcome> p=<0.xx> · review <date>
```
- Lines 2 and 6 are never dropped. Skipping a Top 10 lesson, or one at rung R3 or higher, needs a reason.
- The decision's log line ends with `uses: L-0xx, L-0yy` or `uses: none`. That marker is how lesson use gets counted.

## The record (big, costly or irreversible decisions)
File `decisions/D-YYYY-MM-DD-<slug>.md`. Write and commit it **before the outcome is known**; the commit date is the proof. Nothing above "Review part 1" changes after "decided"; a change is a new record that supersedes the old one. Keep it ≤60 lines; link reports instead of copying them.

| Field | Content |
|---|---|
| ID, question | One neutral line, as a question, no preferred option |
| Status | proposed → decided → reviewed; superseded by D-… |
| Owner | Who decides, who carries it out |
| Gate | The 7 lines above |
| Options | Including "do nothing / wait", each with why rejected |
| Outside view | Reference class and base rate, with source; your own history once you have ≥6 similar cases |
| Forecasts | 1-3 checkable claims: probability in 5% steps, resolve-by date, resolution rule, who made it |
| Confidence | H/M/L and what limits it |
| Would change our mind | Observations that would reverse it |
| Kill criteria | A state and a date |
| Known at the time | Key facts with grades |
| State | Time of day; rested or rushed |
| Decider's words | Quoted |
| Review date | — |
| **Review part 1: process (blind)** | Filled from the record only, before the outcome is added, ideally by someone who did not decide (e.g. `claim-checker`): frame, options, information, reasoning, 0-2 each; pivotal lesson: yes / no / unclear |
| **Review part 2: outcome** | Added after part 1 is saved: outcome; each forecast 1 / 0 / void; Brier score; quadrant (good/bad process × good/bad outcome); lessons to add, change or retire → keeper |

Brier score: (p − outcome)², averaged over forecasts; 0 is perfect, 0.25 is a coin flip. A handful of forecasts is a smoke test, not a skill measure.

---

## EXAMPLE (invented)

**D-YYYY-MM-DD-hosting · Should the product move from a managed platform to self-hosted servers this quarter?**
Status: decided · Owner: founder decides; tech lead carries it out
```
GATE · Move hosting to self-managed servers this quarter · reversible: partly
1 Decision and reversibility: migrate the app and database; moving back costs ~2 weeks
2 Lessons: L-002 "trial on the real job, then buy" honoured: one service moved first for 2 weeks · uses: L-002
3 Pass / kill line: p95 latency ≤ today's and hosting bill −30% by YYYY-MM-DD
4 Premortem: database migration loses writes → dry run on a copy, rollback plan written
5 Key claim: "bill drops 40%" · grade C3 (vendor calculator) · checked against source: yes
6 Decider: "Go, but only after the two-week trial passes." · recorded in this file
7 Expect: bill −30% or more p=0.60 · review YYYY-MM-DD
```
Options: stay (rejected: cost grows with usage) · move now (chosen) · wait a quarter (rejected: contract renewal date).
Outside view: of 5 similar migrations found in post-mortems, 3 hit their cost goal (research/YYYY-MM-DD-hosting.md §6).
Forecasts: F1 bill −30% by YYYY-MM-DD p=0.60 (resolved by the invoice) · F2 no data loss p=0.95.
Kill criteria: p95 latency 20% worse for 7 days after cut-over → move back.
Review part 1 (blind): frame 2 · options 2 · information 1 · reasoning 2 · pivotal lesson: yes
Review part 2: F1 = 1, F2 = 1 · Brier 0.08 · good process / good outcome · L-002 → actioned
