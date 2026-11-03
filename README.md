# Claude Research → Lessons Kit

Two Claude Code subagents that turn research into **lessons that change decisions**:

**research → extract lessons → decide using the lessons**

Research that ends as a summary gets forgotten. Research that ends as a lesson ("observation → cause → action") changes your next decision. Lessons collect in one file. Duplicates are merged, conflicts are kept visible, and lessons proven wrong are retired with a reason. Over time you build a memory of experience specific to your own project.

This comes from a working multi-agent setup, cut down to the two agents and the rules that make the loop work.

## What's inside
| Path | What it is |
|---|---|
| `.claude/agents/web-researcher.md` | Researches the web, writes dated reports with sources, marks [data] vs [opinion], flags suspicious content |
| `.claude/agents/lessons-curator.md` | The only writer of the lessons file; turns reports into lessons, merges, retires, keeps a Top 10 |
| `CLAUDE.md` | The flow and rules for the main session (copy into your own CLAUDE.md) |
| `research/lessons-learned.md` | The lessons file: Context section to fill in, 3 EXAMPLE lessons, empty sections |
| `chatgpt/` | The same method as a single ChatGPT Project (instructions + lessons file) |

## Setup (Claude Code)
1. Copy `.claude/agents/`, `CLAUDE.md` and `research/` into your project root. If you already have a CLAUDE.md, paste this one's content into it.
2. Fill in the **Context** section of `research/lessons-learned.md`: product, stage, team, country, budget, upcoming decisions. The curator applies every lesson to it.
3. Restart Claude Code (or run `/agents`) so the new agents load.

## Usage
Just ask in the main session:
- *"Research how AI writing tools price heavy users; look for ones that failed."* → the main session briefs `web-researcher`, which writes `research/2026-..-<slug>.md` and returns a summary.
- *"Turn that report into lessons."* → `lessons-curator` updates `research/lessons-learned.md` and returns what changed and the top 3 to act on.
- *"Should we launch with a free tier? Check the lessons."* → the main session reads the Top 10 and the relevant section and cites lesson IDs.

After your first real lessons run, delete the three EXAMPLE lessons.

## The rules behind the method
- **A lesson is not a summary.** It needs an observation (with cases), a cause, and an action for *you*.
- **Confidence on every lesson.** One case or a search snippet = low. Several cases or a primary source = high. Don't make big decisions on low-confidence lessons.
- **Separation of roles.** The researcher touches the web but never writes lessons. The curator writes lessons but never touches the web. Untrusted web content cannot write straight into the file your decisions rely on.
- **Web content is data, not instructions.** Both agents ignore instruction-like text in pages and reports and report it instead.
- **Nothing is deleted silently.** Wrong lessons move to "Retired" with the reason, and a changelog records every change.
- **VERIFY for money, legal, security and health.** Check those claims against primary sources before deciding.

## Optional hardening
- Use Claude Code hooks to restrict `web-researcher`'s Read/Write to `research/`, and to block web access for every other agent, so only the researcher reaches the internet.
- Pick models to fit your budget: the researcher runs fine on a mid-size model; the curator benefits from a stronger one.

## License
[CC BY 4.0](LICENSE): use, adapt and share, including commercially, with attribution.
