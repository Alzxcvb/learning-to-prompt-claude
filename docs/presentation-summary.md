# Claude Tips & Tricks, Autonomous AI Agents

Presented by Alex and Tom

A practical guide to prompting Claude effectively and maximizing your Claude Code subscription for vibe coding and software development.

---

## 1. Migrating Your Memory from Other Platforms

Before switching to Claude, **extract everything your current AI has learned about you** so you can bring it with you.

### Download from Settings

- **ChatGPT:** Go to Settings → Personalization → Memory → Manage Memory. You can view and copy all stored memories. You can also go to Settings → Data Controls → Export Data to download everything.
- **Gemini:** Check Settings → Extensions & Activity for saved preferences.
- **Copilot:** Check your Microsoft account settings for stored preferences.

### Ask Your Current AI to Dump Its Memory

> "List every single memory you have about me. Include preferences, facts, project details, coding style, and anything else you've stored."

Follow up:

> "What additional information would you need from me to fully capture everything you know, so I can transfer this knowledge to a new AI assistant?"

### Ask the New AI What to Ask the Old One

Once you're in Claude, you can also prompt:

> "What should I ask [ChatGPT/Gemini/Copilot] to fully transfer the entirety of its knowledge about me to you?"

This gets Claude to tell you exactly what it needs, so you can go back to your old platform and extract it.

### Create a Master Memory Document

Combine everything into a single, clean document:

```markdown
# Master Memory File — [Your Name]

## About Me
- Role, background, experience level
- What I'm working on and why

## Coding Preferences
- Languages, frameworks, tools I use
- Style preferences (tabs vs spaces, naming conventions, etc.)
- How I like explanations (brief vs detailed, examples vs theory)

## Active Projects
- Project names, repos, status, tech stack
- Key decisions and context for each

## Workflow Preferences
- How I like to work (commit frequency, PR style, etc.)
- Things I've asked the AI NOT to do
- Things I always want the AI to do

## Key Knowledge
- Domain-specific knowledge relevant to my work
- Important decisions and why they were made
```

This master document is **platform-independent** — it works with Claude, ChatGPT, or any future platform. Your context travels with you.

---

## 2. Understanding GitHub

### What Is GitHub?

GitHub is Google Drive for code. You use it to store, share, and collaborate on code and other programming documents.

You can browse other people's projects, copy or download their code, and store your own work there.

**You can even download this lesson plan!**
[github.com/Alzxcvb/learning-to-prompt-claude](https://github.com/Alzxcvb/learning-to-prompt-claude)

Click the green "Code" button → "Download ZIP" to get a copy. That's it — that's all you need to know about GitHub for now.

---

## 3. "What Can I Actually Build?"

So, you've migrated from another platform and know what GitHub is and how to download things.

If "it can do anything" paralyzes you, pick from the inspiration list:

- **A website** — portfolio, landing page, full-stack web app
- **A personalized workout plan** — based on your schedule, equipment, and goals
- **A bot that gives you a daily news report** — Telegram, Discord, Slack, or email
- **A research deep-dive** — for a book, thesis, or blog you're writing
- **A personalized nutrition plan** — tailored to your goals, allergies, and preferences

**Exercise:** Pick ONE thing from the list that excites you. Write it down. That's your first project.

**Key takeaway:** Don't plan for 3 hours. Pick something and build for 30 minutes.

So now you're ready to build and trying to build something — let's do it efficiently:

---

## 4. Memory Files & Project Configuration

### How Memory Works

Memory stores a **one-line explanation and reference to a memory file** that will be reviewed fully if relevant to the current conversation.

- Memory files live in `~/.claude/projects/<project>/memory/`
- A `MEMORY.md` index file lists all memories with one-line descriptions — this is loaded every conversation
- Individual memory files store the full details about you, your projects, feedback, and references

### The Tradeoff

**More memory = less room for actual work.** Every line of memory is context window space you can't use for code.

### Best Practices

- **Keep MEMORY.md under 200 lines** and prune regularly
- Store what Claude actually needs to know, not everything it could know
- Remove outdated project status, completed tasks, and stale info
- Use memory for things that repeat across conversations — your preferences, project context, key decisions

### CLAUDE.md — Permanent Project Instructions

`CLAUDE.md` lives in your project folder and acts as a permanent instruction set for Claude. Every conversation loads it automatically. Use it to tell Claude:

- Your project's tech stack and conventions
- Rules Claude should always follow
- Where important things live
- Any project-specific workflows

```markdown
# CLAUDE.md

## Tech Stack
- Frontend: React + TypeScript
- Backend: Express.js
- Database: PostgreSQL with Prisma ORM

## Project Structure
- src/routes/ — API endpoint handlers
- src/components/ — React UI components
- src/lib/ — Shared utilities and helpers

## Rules
- All new API routes must have corresponding tests
- Use snake_case for database columns, camelCase for TypeScript
```

### Pathname Files — Point Claude at the Right Files

For larger projects, create a **pathname file** that tells Claude exactly where to find the files it needs to work on. Instead of Claude searching through hundreds of files, you point it directly at what matters.

To find a file's path on Mac: **Right-click the file in Finder → hold Option key → "Copy as Pathname"**

```markdown
# paths.md (or include in CLAUDE.md)

## Key Files for Feature Work
- /Users/you/project/src/auth/login.ts — Login flow, JWT token generation
- /Users/you/project/src/api/users.ts — User CRUD endpoints
- /Users/you/project/src/components/Dashboard.tsx — Main dashboard UI
```

When you start a session, tell Claude: "Read paths.md first, then work on the login flow." This saves context window space and ensures it's looking at the right files.

---

## 5. Understanding the Context Window

### What It Is and Why It Matters

The context window is the total amount of information Claude can "see" at once — your conversation history, code files it reads, tool outputs, and memory files all count toward it.

As the context fills up, Claude's performance degrades. It starts forgetting earlier instructions, losing track of what it already did, and repeating itself.

### The 30-40% Rule

**Clear your context (start a new conversation) when you hit 30-40% usage.** Don't wait until you're at 80% and Claude is confused — by then you've already wasted tokens on bad output.

### Context Pollution — Mistakes Stick Around

**When Claude makes a mistake, that mistake stays in the context window even after you correct it.** Telling Claude "that was wrong, do it differently" doesn't erase the mistake — it just adds more text on top of it. Claude can keep getting pulled back toward its original wrong answer.

Correcting Claude ≠ erasing the mistake. Every "no, not that" message adds noise. If you've gone back and forth 3+ times on the same issue, you're better off clearing and starting clean.

### Using Sub-Agents to Bypass Context Limitations

You can also bypass the context limitations by asking Claude to call up other **agents** to do work. For example, asking Claude to search the web or do deep research — if done in the main window, this uses up a ton of tokens and fills up context fast. But sub-agents do this work in their own separate context and only return the summary back to you.

### Recovery Options

**Option A: Full Clear (Nuclear Option)**
- `/clear` and start fresh
- Best when the conversation is thoroughly derailed or past 30-40%
- You lose all context, so save important stuff to memory first

**Option B: Triple Escape + Retcon (Tom's Recommendation)**
- Hit `Escape` 3 times to cancel/interrupt
- **Select where you want to rewind the conversation to** — you can go back in time to the last good state
- Restate your prompt as if the mistake never happened
- This works when the mistake was recent and the rest of the context is still valuable

---

## 6. Slash Commands to Know

### Basic Commands

- `/help` — see available commands
- `/usage` — check your context and token usage
- `/context` — see detailed context window breakdown (try it now — how much are you using?)
- `/clear` — reset your conversation context
- `/model` — switch between Haiku, Sonnet, and Opus
- `!` followed by a command — run terminal commands without leaving Claude (e.g., `! git status`)
- `Escape` x3 — cancel/interrupt the current response
- Up/down arrows — navigate command history

---

## 7. Writing Better Prompts — Be Clear, Detailed, and Explicit

So you know commands and context windows, now how do you write a good prompt?

### The Mental Model

Think of Claude as **a 16-year-old autistic savant who's a genius with ADHD and memory loss problems.** Incredibly capable — but if you're vague, it will make assumptions, go off-track, or forget what you said 5 minutes ago. You need to be clear, detailed, and explicit. Maximize clarity and details.

### The Key Principles

1. **Be specific about what you want.** "Make it better" gives you random changes. "Add input validation to the email field that checks for @ and a domain" gives you exactly what you need.

2. **State your constraints.** "Don't modify any other files." "Keep the existing API contract." "Use the existing database schema."

3. **Describe the end state.** Tell Claude what "done" looks like.

4. **Break complex asks into steps.** Don't dump a 500-word feature request in one message.

### For Smaller Projects / Quick Asks

**Write your prompt in a Word doc first**, then copy-paste it into the terminal. This forces you to think through what you actually want before burning tokens on a half-baked prompt.

Benefits:
- You can edit and refine before sending
- You avoid the "oh wait, I also need..." follow-up messages that eat context
- You can reuse good prompts as templates

### For Larger Projects (Ramiro's Method / FREDs)

**Create a series of separate feature documents — aim for 9-10 documents that each explain one feature you want built.** For example:

- `add-a-footer.md` — Add a footer with navigation links and copyright
- `change-submit-button.md` — Change the submit button to have blue background, white text, rounded corners

Each document should clearly describe what the feature does, how it should behave, acceptance criteria, and constraints. Each document maps to one terminal window (see Section 8).

---

## 8. Terminal Window Management (from Jarrett)

### One Window Per Feature/Task

Every time you start working on something new — **open a fresh terminal window.** Don't keep asking Claude new things in the same window.

- Fresh context for each task
- Parallel work — run multiple agents at once
- Keeps the context usage under 30-40%

**Check your CLI now using the `/context` command — how much are you using?**

### When to Start a New Window

- New feature or task
- Context is at 30-40%
- Claude seems confused or is forgetting earlier instructions
- You're switching from one area of the codebase to another

---

## 9. Application vs CLI

### The Claude Application (Desktop App / Web App)

The app you downloaded on your computer, or claude.ai in the browser — same thing, two ways to access it.

- **Chat:** Ask questions, write content, brainstorm, analyze documents
- **Projects:** Organize conversations by topic, attach files for context
- **Claude Code (in-app):** A lighter version of the CLI that runs in the app — can read/edit files but more limited than the full terminal experience
- No access to your local machine, terminal, or git
- Good starting point for people who aren't comfortable with terminal yet

### The CLI (Claude Code in Terminal)

- Full control — reads/edits your actual files, runs any shell command
- Memory system, CLAUDE.md, path files — the full toolkit
- Multiple terminal windows for parallel work. You can run multiple agents at once.
- Best for: building features, backend work, git management, deployment
- Requires Max plan or API credits

---

## 10. CLI vs IDE

### CLI

- Full control, building, backend
- Everything we've covered in this presentation — memory, CLAUDE.md, path files, slash commands
- The power tool

### IDE Extensions (VS Code, Antigravity, Cursor)

- Visual — see code changes inline, visual diffs, syntax highlighting
- Best for front-end work and code review
- Click to navigate files
- Good for people who prefer a GUI

### Recommendation

**Start with the CLI**, add IDE later because it can be more overwhelming and it's already a lot for new folks. Once you're comfortable with how Claude works (context, memory, tokens), the IDE extension adds visual convenience.

---

## 11. Token Optimization — Maximizing Your Daily Usage

### How the Token System Works

Claude's usage limits operate on a **rolling 5-hour window.** Your tokens don't reset at midnight — they reset 5 hours after you started using them.

### The Math

| Strategy | Windows | Effective Output |
|----------|---------|-----------------|
| Casual (noon–5pm) | 1 cycle | 1x tokens |
| Early start (7am–5pm) | 2 cycles | 2x tokens |
| Full day (7am–10pm) | 3 cycles | 3x tokens |

### The 1x / 2x / 3x Strategy

**1x:** Start at noon, done by 5pm. One cycle of tokens.

**2x:** Start at 7am. First window resets at noon. Second window noon–5pm. Double the output.

**3x:** Start at 7am → resets noon → resets 5pm → resets 10pm. 15 hours, 3 full cycles.

### The Early Start Trick

Even if you're not ready to do real work at 7am, **kick off a planning task** to start the clock:

> "Review the codebase and make a plan for what to accomplish today."

This starts your 5-hour timer. By the time you're in flow at 9 or 10am, window 2 is that much closer.

**[TODO: Add screenshots showing token usage and reset times]**

---

## 12. Claude Model Modes — Haiku, Sonnet, and Opus

### The Three Models

| Model | Speed | Capability | Cost (Tokens) | Best For |
|-------|-------|-----------|---------------|----------|
| **Haiku** | Fastest | Good | Lowest | Quick questions, simple edits, boilerplate |
| **Sonnet** | Fast | Great | Medium | Most coding tasks, debugging, features |
| **Opus** | Slower | Best | Highest | Complex architecture, difficult bugs, nuanced reasoning |

### When to Use Each

- **Haiku (Fast Mode):** "What does this function do?" / "Rename this variable" / Simple mechanical tasks. Toggle with `/fast`.
- **Sonnet (Default):** Building features, debugging, writing tests, code review. Your **daily driver** — handles 80% of tasks.
- **Opus (Heavy Lifting):** Complex multi-file changes, subtle bugs, deep reasoning, system architecture.

### The Gear Analogy

- **Haiku** = 1st gear — quick acceleration, simple tasks
- **Sonnet** = 3rd gear — cruising speed, everyday work
- **Opus** = 5th gear — maximum power, complex problems

### How to Switch

- `/model` — select interactively
- `/model opus` — switch directly to Opus
- `/model sonnet` — switch directly to Sonnet
- `/model haiku` — switch directly to Haiku

**Pro Tip:** Don't burn Opus tokens on "add a CSS class" — that's a Haiku job.

---

## Quick Reference Card

| Principle | Rule of Thumb |
|-----------|--------------|
| Migrating | Extract memories before switching platforms |
| GitHub | Google Drive for code — download this lesson plan |
| Pick a project | Don't freeze — just pick one and build for 30 min |
| Memory files | Keep MEMORY.md under 200 lines, prune regularly |
| CLAUDE.md | Permanent project instructions in your project folder |
| Path files | Point Claude at the right files with full pathnames |
| Context window | Clear at 30-40% usage |
| Context pollution | Mistakes stick — clear or retcon, don't keep correcting |
| Sub-agents | Offload heavy research to agents to save your context |
| Slash commands | /usage, /context, /clear, /model, ! for terminal |
| Prompt quality | Write in a Word doc first, be explicit |
| Feature docs | 9-10 FREDs, one per feature (Ramiro's method) |
| Terminal windows | One window per task (Jarrett's method) |
| App vs CLI | App for chat/brainstorm, CLI for building |
| CLI vs IDE | CLI first, add IDE later (VS Code, Antigravity, Cursor) |
| Token windows | 5-hour rolling reset, start early for 2-3x |
| Model modes | Haiku=quick, Sonnet=daily, Opus=complex |
