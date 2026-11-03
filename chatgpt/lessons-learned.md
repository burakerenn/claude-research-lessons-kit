# Lessons learned

**Purpose:** turn evidence into lessons that change decisions, in technology, startups, business, engineering and AI. Evidence means research, your own experiments, project results, mistakes and wins.
**How to use:** before a decision that matters, read the Top 10, then grep this file for the decision's trigger words. Pull 1-3 lessons, quote their Action line, and mark the decision `uses: L-xxx` (or `uses: none`).
**Writer:** the keeper only (`lessons-keeper`, or the LESSONS command in ChatGPT). One lesson per edit; the file is never regenerated.
**Last updated:** YYYY-MM-DD

---

## Context (fill this in once, keep it current)
Every lesson is applied to this context, so a lesson that is true in general but wrong for you gets flagged.
- **Who:** <you / your team: size, roles, skills>
- **What you build:** <product or service, for whom, business model>
- **Stage:** <idea / prototype / beta / paying users / scaling>
- **Market and location:** <where you sell, where the company is or will be registered>
- **Stack and tools:** <languages, platforms, AI models and APIs, no-code tools, hardware>
- **Constraints:** <budget, runway, time per week, team size, rules you must follow, things you will not do>
- **Upcoming decisions:** <the next few choices these lessons should inform>

---

## Areas and sub-topics
Lessons live in one of these areas. Put the matching sub-topic in the lesson's **Area** field (e.g. `Engineering › scope`). Add sub-topics when you need them; keep the seven areas. Topics outside these areas get no lesson; the report keeps the finding.

| Area | Sub-topics |
|---|---|
| **Technology** | stack choice · build vs buy · vendors and SaaS · tooling · infrastructure and cloud · open source · technical debt · migrations |
| **Startup** | problem-solution fit · validation and demand tests · MVP scoping · positioning · pivots · fundraising · founders and equity · timing |
| **Business** | pricing · unit economics · go-to-market · marketing and audience · sales · customers and churn · partnerships · launch |
| **Engineering** | architecture · scope and estimation · quality and testing · delivery and DevOps · hardware and DFM · prototyping · reliability · documentation |
| **AI** | model choice · agents and workflows · prompts and context · evaluation · cost and tokens · data · privacy and safety · UX of AI features |
| **Legal, security and risk** | contracts and IP · licences · compliance · security · certification · supply chain · insurance |
| **Team and operations** | hiring · roles and process · communication · remote work · outsourcing · suppliers · finance ops |

---

## How lessons are written

A summary says what happened. A lesson says what happened, why, and **what you will do differently**. No action, no lesson.
A lesson counts as *learned* only when something changed (a checklist, a prompt, a tool) and a later case showed it worked.

### Fields (one-word names, so grep works)
| Field | What goes in it |
|---|---|
| `### L-0xx <title>` | The title is a claim ("Unfrozen scope makes builds run late"). IDs are never reused. |
| Area | Area › sub-topic from the table above |
| Type | **Do** (repeat what worked) · **Avoid** (a failure pattern) · **Watch** (an early warning sign) |
| When | The trigger in plain words: "before paying for a tool", "when a deadline moves" |
| Observation | What happened; two contrasting cases where possible |
| Cause | The mechanism, not a restatement |
| Action | What you do, concrete enough to check later. Your own words, never copied from a source quote |
| Limits | When it does not hold; counter-evidence; conflicting lesson IDs |
| Evidence | Report path + section, or `retro` / `experiment` / `experience` / `expert`; access: full / part / snip |
| Grade | Source letter × claim number for the central claim, e.g. `B2` (legend below) |
| Likelihood | Only when the action rests on a forecast: word + number, e.g. "likely (55-75%)" |
| Status | watch → identified → actioned → embedded → verified; or retired (ladder below) |
| Rung | R0-R5: how the lesson is built in (ladder below) |
| Embedded in | The file, checklist, prompt or tool that now carries it |
| Owner | One role who keeps it alive |
| Review by | Principles 12 months; area lessons 6 months; tools, AI, prices and security 3 months |
| Re-test by | Avoid lessons only: a date for one cheap check that the avoid still holds |
| Related | Supporting, refining or conflicting IDs |
| Class | **public** (may be shared) · **internal** (your context, no personal facts) · **personal** (facts about a person; never shared) |
| Dates | Added / updated |

Use counts are not stored here. Count them from the `uses:` markers in your decisions.
Money, legal and security lessons add a line `VERIFY: <the exact claim to check>`; they are checked before they move past identified.

**Grade.** Source: **A** primary and authoritative for this fact (incl. your own measurement) · **B** independent and methodical · **C** credible but interested or thin (a vendor on its own product) · **D** weak (anonymous, forum) · **E** unreliable · **F** cannot judge (incl. snippet-only). Claim: **1** confirmed (two independent origins, or one A source with first-hand authority) · **2** probably true · **3** possibly true (max for F sources) · **4** doubtful · **5** improbable · **6** cannot judge.

### Status ladder (what moves a lesson)
| Status | Entry condition | Proof |
|---|---|---|
| watch | One report, vendor-only, or thin but plausible. Not eligible for the Top 10 | Report path |
| identified | Passes the admission gate; has cause, action, owner | ≥2 independent origins, or your own outcome |
| actioned | Done once, or a decision gate honoured it | Decision with `uses: L-xxx` |
| embedded | A file or tool carries it at R2 or higher | Path + line |
| verified | A later outcome, retro or test showed the effect | Decision review or retro ID |
| retired | Wrong, merged, superseded, expired, or retired by outcome | Entry in Retired lessons, with reason |

If the failure comes back while the lesson exists: back to identified ("embed failed"), next embed one rung higher.

### Rung ladder (how it is built in; stronger is higher)
| Rung | Meaning |
|---|---|
| R5 Remove | The tool or path that allowed the failure is gone |
| R4 Enforce | A hook, deny rule or check that blocks it |
| R3 Gate | A required field someone checks (a line in the decision gate) |
| R2 Scoped | A line in one agent prompt, skill or checklist, at its trigger |
| R1 Always-loaded | A line in CLAUDE.md or similar, read every session |
| R0 Reference | Only in this file |

A lesson broken twice moves up one rung. Money, sending, publishing, deleting and secrets go straight to R4 or R5. A block that fires wrongly or nags gets narrowed.

---

## Top 10 lessons now
The lessons that matter most for your **upcoming decisions**. Changed only with a stated reason. Watch lessons are not eligible.

> The lessons below are EXAMPLES. They show the format, not real research. Retire them after your first real keeper run.

1. L-001 (EXAMPLE) Unfrozen scope makes builds run late.
2. L-002 (EXAMPLE) Tools chosen from demos get dropped; a trial on the real job predicts use.
3. L-003 (EXAMPLE) LLM features without an eval set regress silently.

---

## Technology

### L-002 (EXAMPLE) Tools chosen from demos get dropped; a trial on the real job predicts use
- Area: Technology › vendors and SaaS · Type: Do · Class: public
- When: before paying for a tool, platform or service
- Observation: two tools chosen from reviews and demos were dropped within a month; one trialled on a real workload first is still in use.
- Cause: demos show general features; the bottleneck is one specific job that demos rarely cover.
- Action: write down the one job the tool must do, run it on real data in a trial, then buy.
- Limits: for cheap tools the trial may cost more than a wrong purchase.
- Evidence: EXAMPLE (experience), no real source
- Grade: – · Status: actioned · Rung: R2 · Embedded in: purchase checklist (EXAMPLE)
- Owner: whoever buys tools · Review by: YYYY-MM-DD · Related: –
- Added YYYY-MM-DD · Updated –

## Startup

## Business

## Engineering

### L-001 (EXAMPLE) Unfrozen scope makes builds run late
- Area: Engineering › scope and estimation · Type: Avoid · Class: public
- When: starting any build with a deadline
- Observation: three projects that took new requests during the build finished 2-3x late; one that froze scope on day one finished on time.
- Cause: each mid-build change reset work in progress and needed re-testing.
- Action: write the scope down with a freeze date; later requests go to a "next round" list unless they block the goal.
- Limits: less true for exploration work, where learning is the goal. Four cases, one team: rival cause is team size.
- Evidence: EXAMPLE (retro), no real source
- Grade: – · Status: identified · Rung: R0 · Embedded in: –
- Owner: project lead · Review by: YYYY-MM-DD · Re-test by: YYYY-MM-DD · Related: L-003
- Added YYYY-MM-DD · Updated –

## AI

### L-003 (EXAMPLE) LLM features without an eval set regress silently
- Area: AI › evaluation · Type: Watch · Class: public
- When: adding or changing a prompt, model or retrieval step in a product
- Observation: a prompt tweak that fixed one complaint broke two other cases; nobody noticed for three weeks.
- Cause: LLM changes are non-local; without fixed cases there is nothing to compare against.
- Action: keep 20-50 real cases with expected outcomes; run them on every prompt or model change; a drop blocks the change.
- Limits: a tiny eval set gives false confidence; grow it from production failures.
- Evidence: EXAMPLE (retro), no real source
- Grade: – · Status: embedded · Rung: R4 · Embedded in: CI eval step (EXAMPLE)
- Owner: AI feature owner · Review by: YYYY-MM-DD · Related: L-001
- Added YYYY-MM-DD · Updated –

## Legal, security and risk

## Team and operations

---

## Open questions
Evidence that would create, confirm or overturn a lesson. Each one can become a research brief or an experiment.
- Q-001 

## Decision log (small decisions; big ones get a file in `decisions/`)
| Date | Decision | uses: | Outcome (fill in later) |
|---|---|---|---|
|  |  | L-… / none |  |

## Retired lessons
Wrong, merged, superseded or expired lessons, with the reason and date. Never deleted silently.

## Changelog
One line per keeper run: date · change list (`L-0xx ADD|UPDATE|MERGE|SPLIT|SUPERSEDE|RETIRE|NOOP: source`).
- YYYY-MM-DD · File created from the template, 3 EXAMPLE lessons.

<!-- When this file passes about 150 lines of lessons or 16,000 characters, split it: see research/lessons/INDEX.md. -->
