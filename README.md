# Work-OS

A private career record you keep by talking to Claude Code. You say what happened. Claude files it, spots patterns, and turns it into meeting prep and reviews, with the dates and quotes to back them up.

You never have to fill in a template or edit a file.

## Keep it private

This record will hold performance reviews, feedback, pay and your own candid notes. Your copy must be private.

- Don't fork this repository. A fork of a public repository is public, and you can't make it private.
- Claude reads these files to help you, so their content is sent to Anthropic. Check your employer's rules before you put work information in a personal account.

## Set it up

You need a paid Claude subscription. The desktop app is the easiest way in.

### 1. Get your copy

Pick one.

**Just on your computer (simplest, no GitHub account needed).** On this page, click **Code**, then **Download ZIP**. Unzip it and move the folder somewhere you'll keep it, such as Documents. Back it up the way you back up your other files.

**On GitHub, with history and an online backup (free GitHub account).**

1. On this page, click **Use this template**, then **Create a new repository**.
2. Name it, choose **Private**, and click **Create repository from template**.
3. Install [GitHub Desktop](https://desktop.github.com) and sign in. Choose **File > Clone Repository**, pick your new repository, choose where to keep it, and click **Clone**.
4. Your files change only on your computer until you back them up. To do that, type a short note in **Summary**, click **Commit to main**, then **Push origin**.

### 2. Open it in Claude

1. Install the [Claude desktop app](https://code.claude.com/docs/en/desktop-quickstart) and sign in.
2. Open the **Code** tab.
3. Under the message box, choose **Local**, then click the project folder control, choose **Open folder…** and pick your Work-OS folder.
4. Claude may ask before it changes a file. Read the change and approve it if it looks right.

If you use a terminal, open the folder there and run `claude`.

### 3. Run setup

Type `/setup`. Claude should offer three short interviews: who you are, this year's goals, and your job. Each takes 15 to 20 minutes. Do one now and the rest later, or skip it and start talking. Setup makes the advice better, but saving works without it.

If Claude says it doesn't know that command, you opened a different folder. Go back to step 2.

### Your first week

- Once a day, say one thing that happened: something you finished, something someone told you, or a decision you made.
- On Friday, paste your status update, ticket list or calendar for the week and say "file this".
- Then ask, "What did you notice?"

## Use it

Talk normally. One message can hold several things.

> Shipped the vendor dashboard Friday, it replaced a 6 hour weekly report. Dana told me to lead with the answer. I turned down the migration because I don't want to manage people. Energy's about a 4 out of 10.

Claude files the win, the feedback, the decision and the check-in, then tells you if something is becoming a pattern or conflicts with what you said you wanted.

| When | What to say |
|---|---|
| Something happens | Just say it |
| Once a week | Paste a weekly summary, ticket list or status note and say "file this" |
| Once a month | `/monthly-log` |
| Before a 1:1 | "Prep me for my 1:1 with Dana" |
| End of quarter, mid-year, year-end | `/career-review` |
| Something feels off | "Where am I drifting?" |
| New job, manager or goals | `/setup` |

The weekly drop is the easiest habit to keep. Most of the record can come from it.

If you go quiet for months, start again from today. There is nothing to catch up on.

## What's in the folder

| File or folder | What it is |
|---|---|
| `CLAUDE.md` | The one page of instructions Claude follows. You can change it, but you don't need to. |
| `.claude/skills/` | The three commands: setup, monthly log, career review. The `.claude` folder is hidden on most computers; you don't need to open it. |
| `.claude/settings.json` | Turns off Claude Code's automatic memory for this folder, so what it learns about you is kept in these files |
| `capture/` | Your logs, one file per kind per year, and their formats |
| `uploads/` | Documents you hand over |
| `examples/` | Made-up entries that show useful detail |

Claude creates the rest as you go: `current_state.md`, `profile.md`, `archive.md`, `foundation/`, `goals/`, `synthesis/` and `reviews/`.

## Only if you used the first version

Your entries stay readable. Copy the new `CLAUDE.md`, `.gitignore`, `.claude/skills/`, `.claude/settings.json`, `capture/README.md`, `uploads/README.md` and `examples/` into your folder. Don't use the old slash commands after that; some write to old files. Then tell Claude:

> Move my record to the layout in CLAUDE.md. Copy first, show me the plan, and don't delete anything until I say so.

## License

MIT. See [LICENSE](LICENSE).
