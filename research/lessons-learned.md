# Lessons learned

**Purpose:** turn evidence into lessons that change decisions, in technology, startups, business, engineering and AI. Evidence means research, your own experiments, project results, mistakes and wins.
**How to use:** before any decision that matters, read the Top 10 and the area it belongs to. Cite lesson IDs when you decide.
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
Lessons live in one of these areas. The sub-topics are tags: put the matching one in the lesson's **Area** field (e.g. `Engineering › scope`). Add sub-topics when you need them; keep the areas as they are so the file stays navigable.

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

### A lesson is not a summary
A summary says what happened. A lesson says what happened, why it happened, and **what you will do differently**. If there is no action, it is a note, not a lesson.
- Weak: "Many projects ran late."
- Strong: "Projects whose scope was not frozen before the build started ran 2-3x over time (A, B, C) → each late request reset the work in progress → freeze scope at a fixed date; new requests go into the next round."

### Fields
| Field | What goes in it |
|---|---|
| **ID** | L-001, L-002, … Never reused, even after retirement. |
| **Title** | The action in one line. |
| **Area** | Area › sub-topic from the table above. |
| **Type** | **Do** (repeat what worked) · **Avoid** (a failure pattern) · **Watch** (an early warning sign) |
| **When it applies** | The situation that should trigger this lesson, e.g. "before signing a vendor contract" or "when a deadline moves". |
| **Observation** | What happened, with the cases named. |
| **Cause** | Why it happened: the mechanism, not a restatement. |
| **Action** | What to do, concrete enough that you could check later whether you did it. |
| **Limits** | When it does *not* hold, plus any counter-evidence. |
| **Evidence** | Sources, each with its type: `research` (report), `experiment` (your own test), `retro` (review of your own project), `experience` (first-hand, unwritten), `expert` (someone who knows). |
| **Confidence** | **high** = several independent cases or a primary source · **medium** = a few cases · **low** = one case, a snippet, or unverified numbers |
| **Status** | **candidate** (new, one source) → **active** (confirmed by a second independent case or a primary source) → **retired** (proven wrong or outdated, with the reason) |
| **Review by** | A date to re-check. Use it for fast-changing topics: prices, model capabilities, tools, laws, markets. Leave it empty for stable lessons. |
| **Related** | Other lesson IDs that support, refine or conflict with this one. |
| **Dates** | Added / updated. |

### Quality gate (every lesson must pass)
1. **Actionable:** the Action names something you can do or check.
2. **Specific:** it names when it applies; "always" and "never" need strong evidence.
3. **Evidenced:** every claim traces to a listed source; nothing is invented.
4. **Not obvious:** if everyone already knows it, it only stays when you keep breaking it.
5. **Scoped to your context:** it says when it only holds for others (bigger teams, other countries, more money).
6. **Flagged:** money, legal and security lessons say **VERIFY before deciding** and name the claim to check.

---

## Top 10 lessons now
The ten lessons that matter most for your **upcoming decisions**. Rewritten after every curation run.

> The three lessons below are EXAMPLES. They show the format, not real research. Delete them after your first real curation run.

1. [L-001](#l-001-example-freeze-scope-before-the-build-starts) (EXAMPLE) Freeze scope before the build starts; new requests go to the next round.
2. [L-002](#l-002-example-adopt-a-tool-or-saas-only-after-a-trial-on-the-real-workload) (EXAMPLE) Adopt a tool or SaaS only after a trial on the real workload.
3. [L-003](#l-003-example-ship-an-llm-feature-only-with-an-eval-set) (EXAMPLE) Ship an LLM feature only with an eval set; without one, prompt changes regress silently.

---

## Technology

### L-002 (EXAMPLE) Adopt a tool or SaaS only after a trial on the real workload
- **Area:** Technology › vendors and SaaS
- **Type:** Do
- **When it applies:** before paying for a tool, platform or service.
- **Observation:** two tools chosen from reviews and demos were dropped within a month. The one trialled on a real workload first is still in use.
- **Cause:** reviews and demos test general features; your bottleneck is one specific job, which demos rarely cover.
- **Action:** write down the one job the tool must do, run it on real data in a trial, then buy.
- **Limits:** for cheap tools the trial may cost more than a wrong purchase.
- **Evidence:** EXAMPLE (experience), no real source.
- **Confidence:** low (example) · **Status:** candidate · **Review by:** – · **Related:** –
- **Added:** YYYY-MM-DD

## Startup

## Business

## Engineering

### L-001 (EXAMPLE) Freeze scope before the build starts
- **Area:** Engineering › scope and estimation
- **Type:** Avoid
- **When it applies:** starting any build with a deadline.
- **Observation:** three projects that accepted new requests during the build finished 2-3x late. A fourth that froze scope on day one finished on time.
- **Cause:** each mid-build change reset work in progress and needed re-testing; the cost grew with every change.
- **Action:** write the scope down and set a freeze date. Changes after it go to a "next round" list unless they block the goal.
- **Limits:** less true for exploration or research work, where learning is the goal.
- **Evidence:** EXAMPLE (retro), no real source.
- **Confidence:** low (example) · **Status:** candidate · **Review by:** – · **Related:** L-003
- **Added:** YYYY-MM-DD

## AI

### L-003 (EXAMPLE) Ship an LLM feature only with an eval set
- **Area:** AI › evaluation
- **Type:** Watch
- **When it applies:** adding or changing any prompt, model or retrieval step in a product.
- **Observation:** a prompt tweak that fixed one complaint broke two other cases; nobody noticed for three weeks because there was no test set.
- **Cause:** LLM behaviour changes are non-local: a change for one input shifts outputs for others, and without a fixed set of cases there is nothing to compare against.
- **Action:** before the first release, collect 20-50 real cases with expected outcomes. Run them on every prompt or model change. A drop in the pass rate blocks the change.
- **Limits:** a tiny eval set gives false confidence; grow it from production failures.
- **Evidence:** EXAMPLE (retro), no real source.
- **Confidence:** low (example) · **Status:** candidate · **Review by:** – · **Related:** L-001
- **Added:** YYYY-MM-DD

## Legal, security and risk

## Team and operations

---

## Open questions
Evidence that would create, confirm or overturn a lesson. Each one can become a research brief or an experiment.
- 

## Decision log (optional)
Close the loop: record which lessons a decision used, then come back and note the outcome. Outcomes become new evidence.
| Date | Decision | Lessons used | Outcome (fill in later) |
|---|---|---|---|
|  |  |  |  |

## Retired lessons
Lessons proven wrong or outdated, with the reason and the date. Never deleted, so you can see why your view changed.

## Changelog
- YYYY-MM-DD · File created from the template, 3 example lessons.
