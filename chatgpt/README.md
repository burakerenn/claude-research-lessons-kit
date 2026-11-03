# Research → Lessons Kit (for ChatGPT Projects)

The same method as the Claude Code kit in this repo, set up as a single ChatGPT Project. It turns evidence into **lessons that change decisions**, in any domain: a product, a research project, a career, an engineering build, a team, a hobby or personal habits.

**research / your own results → lessons → decisions → outcomes → better lessons**

## Files
| File | Purpose | Where it goes |
|---|---|---|
| `project-instructions.md` | The assistant's working rules (5 commands) | Project → **Instructions** (paste everything below the line) |
| `lessons-learned.md` | The lessons file: Context, fields, quality gate, 3 EXAMPLE lessons | Project → **Files** (upload) |
| `../research/retro-template.md` | Optional: a retro form you can fill in yourself | Keep it handy, or use the RETRO command |

## Setup (5 minutes)
1. In ChatGPT, create a new **Project**.
2. Paste everything below the line in `project-instructions.md` into the project **Instructions**.
3. Fill in the **Context** section of `lessons-learned.md`: who you are, domain(s), goals, constraints, upcoming decisions. Rename the sections to fit your domain.
4. Upload `lessons-learned.md` to the project **Files**.

## Commands
Start a message with one of these:
- **`RESEARCH <topic>`**: a dated web report with sources, [data] vs [opinion], success **and** failure cases, and lesson candidates. It does not change the lessons yet.
  - `RESEARCH Why do small open-source projects lose contributors?`
- **`RETRO <what>`**: the assistant interviews you about something you did (a project, test, purchase, launch, failure) and writes a retro.
  - `RETRO Last month's attempt to switch our team to weekly planning`
- **`LESSONS`**: turns the latest report or retro into lessons and returns the **complete** updated file.
- **`DECIDE <question>`**: lists the lessons that apply, where they conflict and what evidence is missing, gives a recommendation, and gives you a Decision log row.
  - `DECIDE Take the job offer, or keep freelancing for 6 more months?`
- **`REVIEW`** (about monthly): flags stale, duplicate, conflicting and unconfirmed lessons and returns a cleaned-up file.

Without a command it chats normally, but cites lesson IDs when they are relevant. Write in any language.

## Important: keep the file current
ChatGPT cannot edit a file you uploaded to a project. After every **LESSONS** or **REVIEW** run:
1. Download the new `lessons-learned.md`. If you got a code block instead, copy it into the file.
2. Delete the old file from the project Files and upload the new one.

This is the only manual step. If you skip it, the next chat sees the old lessons.

## First run
1. Fill in the Context and upload the file.
2. Do one `RESEARCH` on a question you care about, and one `RETRO` on something you did recently.
3. Run `LESSONS` after each. Check that every lesson has a cause and an action, and push back if you only get summaries.
4. Delete the 3 EXAMPLE lessons and upload the file again.
5. Before your next real decision, try `DECIDE`. Later, add the outcome to the Decision log and run `LESSONS` again.

## Limits
- Web search sometimes reads only a snippet. Findings marked "(snippet)" deserve less trust.
- Project Instructions have a length limit. Keep additions short, or put extra rules in a project file.
- If the assistant drifts from the rules, say: "Redo this following the LESSONS rules in the instructions."
- Not tested on every ChatGPT plan. If it cannot create files, it returns the full file as a code block.
