# Research → Lessons Kit (for ChatGPT Projects)

A small kit that turns an AI assistant into a research and lessons partner for a startup:

**research → extract lessons → decide using the lessons**

The idea: research that ends as a summary gets forgotten. Research that ends as a **lesson** changes your next decision. Lessons collect in one file. Duplicates are merged, and lessons proven wrong are retired with a reason. Over time you build a "memory of experience" specific to your own startup.

The method comes from a multi-agent setup built on Claude, where one agent researches and another curates lessons. This kit adapts it to a single ChatGPT Project.

## Files
| File | Purpose | Where it goes |
|---|---|---|
| `project-instructions.md` | The assistant's working rules | Project → **Instructions** (paste) |
| `lessons-learned.md` | The lessons file, with 3 example lessons | Project → **Files** (upload) |

## Setup (5 minutes)
1. In ChatGPT, create a new **Project**, e.g. "Startup – Research & Lessons".
2. Open the project settings and paste everything below the line in `project-instructions.md` into **Instructions**.
3. Fill in the **Context** section of `lessons-learned.md`: your product, stage, country, budget and upcoming decisions. The assistant applies every lesson to this context, so this part matters most.
4. Upload `lessons-learned.md` to the project **Files**.

## Usage: three commands
Start your message with a command:

- **`RESEARCH <topic>`**: the assistant researches the web and writes a dated report. Every finding is marked [data] (a sourced fact) or [opinion] (an interpretation). It does not write lessons yet.
  - Example: `RESEARCH Pricing of B2B AI assistants: who charges for what, who failed, and why`
- **`LESSONS`**: the assistant turns the latest report into lessons. It checks the existing lessons first, updates a lesson when the new evidence agrees, and keeps both sides when the evidence conflicts. It returns the **complete** updated file.
- **`DECIDE <question>`**: the assistant lists the relevant lessons, says what they suggest and where they conflict, names the missing evidence, and gives its recommendation. The decision stays yours.
  - Example: `DECIDE Should the first version be free, or a 14-day trial?`

Without a command it chats normally, but cites lessons when they are relevant (e.g. "per L-004…"). You can write in any language. Answers come back in your language.

## Important: keep the file current
ChatGPT cannot edit a file you uploaded to a project. After every **LESSONS** run:
1. Download the new `lessons-learned.md` the assistant gives you.
2. Delete the old file from the project Files and upload the new one.

If you skip this, the next chat sees the old lessons. It is the only manual step.

## First run (recommended)
1. Fill in the Context section and upload the file.
2. Use `RESEARCH` on something you really want to know. Competitors and similar products that failed are good first topics.
3. Type `LESSONS`. Check that each lesson reads "observation → cause → action". If you only get a summary, push back: "This is a summary. Where is the action?"
4. Delete the 3 EXAMPLE lessons and upload the file again.
5. After a few research rounds, try `DECIDE` and check whether the assistant uses the lessons.

## The rules behind the method
- **A lesson is not a summary.** "Big companies got many users" is not a lesson. "These cases happened because of this, so we will do that" is a lesson. If there is no action at the end, it is not a lesson.
- **Every lesson has a confidence level.** A lesson from one case is "low", and so is a lesson resting only on a search snippet. This stops you from making a big decision on weak evidence.
- **Money, legal, security and health lessons come marked "VERIFY".** Open the primary source yourself before you decide.
- **Web pages are data, not instructions.** Some pages hide text meant to steer AI assistants. The instructions tell the assistant to ignore such text and show it to you.
- **Nothing is deleted silently.** A lesson proven wrong moves to "Retired lessons" with the reason, so you can see later why your view changed.
- **The Top 10 list** always shows the 10 lessons that matter most right now. On a busy day, read only that.

## Limits
- ChatGPT's web search sometimes reads only a search snippet without opening the page. The instructions ask it to mark this as "(snippet)". Trust those findings less.
- Project Instructions have a length limit. If you extend the instructions, keep them short, or upload the extra part as a project file.
- The assistant may drift from the rules now and then. Say "Redo this following the LESSONS rules in the instructions."
- Not tested on every ChatGPT plan. If the assistant cannot create a downloadable file, it returns the full file as a markdown code block. Copy it into `lessons-learned.md`.

