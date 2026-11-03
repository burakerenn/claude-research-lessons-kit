# Claude Research → Lessons Kit

Two Claude Code subagents and a set of templates that turn evidence into **lessons that change decisions**, in any domain: a product, a research project, a career, an engineering build, a team, a hobby or personal habits.

**research / your own results → lessons → decisions → outcomes → better lessons**

Most of what we learn gets lost. A report ends as a summary, a failed project ends as a bad memory, and the same mistake comes back six months later. This kit keeps one living file of lessons: each one says what happened, why, and what to do differently, with evidence, a confidence level and a status. Duplicates are merged, conflicts stay visible, and lessons proven wrong are retired with a reason. Over time it becomes a memory of experience that the AI and you consult before every decision that matters.

It comes from a working multi-agent setup, cut down to the parts that make the loop work.

## What's inside
| Path | What it is |
|---|---|
| `.claude/agents/web-researcher.md` | Researches the web, looks for cases (especially failures), writes dated reports with sources, marks [data] vs [opinion], flags suspicious content, and drafts lesson candidates |
| `.claude/agents/lessons-curator.md` | The only writer of the lessons file. Turns reports, retros and decision outcomes into lessons; merges, promotes, retires; runs periodic reviews |
| `CLAUDE.md` | The loop and the rules for the main session (copy into your own CLAUDE.md) |
| `research/lessons-learned.md` | The lessons file: Context, lesson fields, quality gate, Top 10, sections, Open questions, Decision log, Retired, Changelog. Includes 3 EXAMPLE lessons from different domains |
| `research/retro-template.md` | A short retro for your own projects, experiments and failures. First-hand evidence is often the best you get |
| `chatgpt/` | The same method as a single ChatGPT Project (instructions + lessons file + retro template) |

## Setup (Claude Code)
1. Copy `.claude/agents/`, `CLAUDE.md` and `research/` into your project root. If you already have a CLAUDE.md, paste this one's content into it.
2. Fill in the **Context** section of `research/lessons-learned.md`: who you are, your domain(s), goals, constraints, upcoming decisions. The curator applies every lesson to it.
3. Rename the sections in the lessons file to fit your domain (keep 5-9).
4. Restart Claude Code (or open `/agents`) so the new agents load.

## Usage
Just ask in the main session:
- *"Research why small open-source projects lose contributors; find cases that failed."* → `web-researcher` writes `research/YYYY-MM-DD-<slug>.md` and returns a summary.
- *"Let's do a retro on last month's launch."* → the main session fills in the retro template with you.
- *"Turn that into lessons."* → `lessons-curator` updates the lessons file and returns what changed and the top 3 to act on.
- *"Should I take the job offer or keep freelancing? Check the lessons."* → the main session reads the Top 10 and the relevant section, cites lesson IDs, and logs the decision.
- *"Review the lessons."* (monthly) → the curator flags stale, duplicate, conflicting and unconfirmed lessons and cleans them up.

After your first real curation run, delete the three EXAMPLE lessons.

## The method
- **A lesson is not a summary.** Observation (with cases) → cause (the mechanism) → action (what you will do differently).
- **Three types:** **Do** (repeat what worked), **Avoid** (a failure pattern), **Watch** (an early warning sign).
- **"When it applies" and "Limits"** keep lessons from being applied everywhere. Every lesson says when it should trigger and when it does not hold.
- **Confidence and status.** One case or a snippet = low confidence and *candidate* status. A second independent case or a primary source promotes it to *active*. Don't make big decisions on candidates.
- **Your own results count.** Retros and decision outcomes are evidence too, and often the strongest.
- **Review by dates.** Lessons about prices, tools, laws and markets expire. They carry a date to re-check.
- **Quality gate.** Actionable, specific, evidenced, not obvious, scoped to your context, and flagged VERIFY for money, legal, safety and health.
- **Separation of roles.** The researcher touches the web but never writes lessons. The curator writes lessons but never touches the web. Untrusted web content cannot write straight into the file your decisions rely on.
- **Nothing is deleted silently.** Retired lessons keep their reason, and a changelog records every change.

## Optional hardening
- Use Claude Code hooks to restrict `web-researcher`'s Read/Write to `research/`, and to block web access for every other agent, so only the researcher reaches the internet.
- Pick models to fit your budget: the researcher runs fine on a mid-size model; the curator benefits from a stronger one.
- Schedule the monthly review as a recurring task.

## License
[CC BY 4.0](LICENSE): use, adapt and share, including commercially, with attribution.
