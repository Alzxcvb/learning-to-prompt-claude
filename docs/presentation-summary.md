# Claude Tips & Tricks — Presentation Summary

A practical guide to prompting Claude effectively and maximizing your Claude Code subscription for vibe coding and software development.

---

## 1. Transferring from ChatGPT (or Other Platforms) to Claude

If you're coming from ChatGPT, Gemini, Copilot, or another AI assistant, Claude will feel familiar in some ways and very different in others. Here's what to expect.

### What's Similar

- You still type natural language prompts and get AI responses
- You can ask it to write, explain, debug, and refactor code
- It understands context from your conversation history

### What's Different

| ChatGPT / Others | Claude Code |
|-------------------|-------------|
| Web chat interface | Terminal-based CLI (or IDE extension) |
| General-purpose assistant | Purpose-built for software engineering |
| No file access | Reads and edits your actual project files |
| No terminal access | Runs shell commands directly |
| Conversation stays in browser | Conversation lives in your terminal session |
| Memory is automatic/opaque | Memory is file-based and you control it |
| One conversation thread | Multiple terminal windows for parallel work |

### Key Mindset Shifts

1. **Claude works in your codebase, not a sandbox.** When you ask Claude Code to edit a file, it edits the real file on your machine. This is powerful but means you should commit frequently.

2. **You don't need to paste code into the chat.** Claude can read your files directly. Instead of copying code into the prompt, just say "read src/app.js and fix the bug on line 42."

3. **Prompts need to be more precise.** ChatGPT is designed to be conversational and forgiving. Claude Code is more literal — it does exactly what you ask, so vague prompts lead to unexpected changes. (More on this in Section 4.)

4. **Context management is your job.** ChatGPT handles context behind the scenes. With Claude Code, you need to actively manage your context window — clearing it, splitting work across windows, and keeping memory lean.

5. **You control the memory.** Instead of hoping the AI "remembers" you, Claude's memory system is transparent — you can see what it stores, edit it, and prune it.

### Migrating Your Memory — Extracting What Your Old AI Knows About You

Before switching platforms, you should **extract everything your current AI has learned about you** so you can bring it with you. This creates a portable "master memory file" that works with any platform — not just Claude.

#### Step 1: Ask Your Current AI to Dump Its Memory

Open a conversation with ChatGPT (or whatever you're using) and prompt:

> "List every single memory you have about me. Include preferences, facts, project details, coding style, and anything else you've stored."

Review the list. If it looks incomplete, follow up:

> "What additional information would you need from me to fully capture everything you know, so I can transfer this knowledge to a new AI assistant?"

This second prompt is key — it gets the AI to identify gaps in its own memory and ask you to fill them in. Answer its questions, then ask for the updated full list.

#### Step 2: Download Your Memories from the Platform

Most platforms let you export your stored memories:

- **ChatGPT:** Go to Settings → Personalization → Memory → Manage Memory. You can view and copy all stored memories. You can also go to Settings → Data Controls → Export Data to download everything.
- **Gemini:** Check Settings → Extensions & Activity for saved preferences.
- **Copilot:** Check your Microsoft account settings for stored preferences.

Copy or download everything you can find.

#### Step 3: Create a Master Memory Document

Combine everything from Steps 1 and 2 into a single, clean document. Organize it into sections:

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

#### Why This Matters

This master document is **platform-independent.** You can:
- Feed it to Claude's memory system (paste it or ask Claude to save it)
- Bring it to any future AI platform
- Use it as onboarding context for any new tool
- Update it as your preferences evolve

You're no longer locked into any single AI's memory system. Your context travels with you.

### "What Can I Actually Build With This?"

If you're new to AI coding tools, the open-endedness can be paralyzing. Here's a concrete list of things people are building with Claude Code right now — pick one that excites you and start there:

**Websites & Apps**
- Build a personal portfolio website from scratch
- Create a full-stack web app (e-commerce, dashboard, SaaS tool)
- Make a mobile-responsive landing page for your business or side project

**AI & Automation**
- Build an AI agent that answers questions about your company's docs
- Create a Telegram/Discord/Slack bot powered by AI
- Automate email outreach or lead generation workflows
- Build an AI model router that picks the best model for each task

**Personal & Health**
- Generate a detailed nutrition plan tailored to your goals, allergies, and preferences
- Create a personalized workout program based on your schedule and equipment
- Build a habit tracker or personal dashboard

**Research & Analysis**
- Do deep research for a PhD thesis, grant proposal, or market analysis
- Analyze datasets and generate visualizations
- Summarize and cross-reference academic papers

**Productivity & Tools**
- Build internal tools for your team (admin panels, reporting dashboards)
- Create browser extensions or CLI tools
- Automate repetitive tasks (data entry, file processing, report generation)

**Learning & Education**
- Have Claude explain complex codebases to you step by step
- Build interactive tutorials or learning platforms
- Create flashcard apps or study tools

Don't try to figure out "the best" project. **Just pick one and start.** You'll learn more in 30 minutes of building than in 3 hours of planning.

### What Is GitHub?

GitHub is a place where people store and share code and other programming documents. Think of it like Google Drive, but for code. You can browse other people's projects, copy or download their code, and store your own work there.

**Try it now:** Go to [github.com/Alzxcvb/learning-to-prompt-claude](https://github.com/Alzxcvb/learning-to-prompt-claude) — that's this document you're reading right now. Click the green "Code" button and select "Download ZIP" to get a copy. That's it — that's all you need to know about GitHub for now.

### Quick Start for New Users

1. Export your ChatGPT memories (see above)
2. Install Claude Code CLI
3. Navigate to your project folder in the terminal
4. Run `claude` to start a conversation
5. Paste your master memory file and say "Save this to your memory system"
6. Try: "Read the README and summarize what this project does"
7. Try: "List all the files in src/ and explain the project structure"
8. You're already doing things ChatGPT can't do — with all your context intact

---

## 2. Understanding the Context Window

The context window is the total amount of information Claude can "see" at once — your conversation history, code files it reads, tool outputs, and memory files all count toward it.

### Why It Matters

- As the context fills up, Claude's performance degrades. It starts forgetting earlier instructions, losing track of what it already did, and repeating itself.
- Responses slow down and become less accurate once you're deep into a session.

### The 30-40% Rule

**Clear your context (start a new conversation) when you hit 30-40% usage.** Don't wait until you're at 80% and Claude is confused — by then you've already wasted tokens on bad output.

### How to Check

- Use `/usage` in Claude Code to see your current context consumption.
- When you notice Claude forgetting things you told it 10 minutes ago, it's time to clear.

### Pro Tip

Before clearing context, make sure any important decisions or findings are saved to your memory file or committed to code. Once you clear, it's gone.

### Context Pollution — Why Mistakes Stick Around

This is one of the most important things to understand: **when Claude makes a mistake, that mistake stays in the context window even after you correct it.** The wrong code, the bad logic, the incorrect approach — it's all still "visible" to Claude in the conversation history. Telling Claude "that was wrong, do it differently" doesn't erase the mistake — it just adds more text on top of it.

This means Claude can keep getting pulled back toward its original wrong answer, especially as the context fills up and it starts losing track of which instructions are current.

#### What to Do When Claude Goes Off Track

**Option A: Full Clear (Nuclear Option)**
- `/clear` and start fresh
- Best when the conversation is thoroughly derailed or past 30-40% anyway
- You lose all context, so save important stuff to memory first

**Option B: Triple Escape + Retcon (Surgical Option)**
- Press `Escape` three times to cancel/interrupt the current response
- Then **go back and restate your original intent clearly** — essentially retcon the conversation back to the last good state
- Rewrite your prompt as if the mistake never happened
- This works when the mistake was recent and the rest of the context is still valuable

#### The Key Insight

Correcting Claude ≠ erasing the mistake. Every "no, not that" message adds noise to the context. If you've gone back and forth 3+ times on the same issue, you're better off clearing and starting clean than adding another correction on top of the pile.

### Using `!` to Run Terminal Commands

You don't need to leave Claude to run shell commands. **Type `!` followed by your command** to execute it directly from within the Claude Code session:

```
! git status
! npm run test
! ls -la src/
```

This is useful when you want to:
- Check something quickly without breaking your conversation flow
- Run a test to verify Claude's changes worked
- Check git status before asking Claude to commit
- Run any terminal command without opening a separate window

---

## 3. Memory Files — Making Claude Remember (Without Wasting Context)

Claude Code has a persistent memory system that carries information between conversations. This is powerful but has a cost: every memory file gets loaded into your context window at the start of each conversation.

### How Memory Works

- Memory files live in `~/.claude/projects/<project>/memory/`
- A `MEMORY.md` index file lists all memories — this is loaded every conversation
- Individual memory files store details about you, your projects, feedback, and references

### The Tradeoff

**More memory = less room for actual work.** If your MEMORY.md is 200 lines and you have 15 detailed memory files, that's context window space you can't use for code.

### Best Practices

- **Keep memories lean.** Store what Claude actually needs to know, not everything it could know.
- **Prune regularly.** Remove outdated project status, completed tasks, and stale info.
- **Use memory for things that repeat across conversations** — your preferences, project context, key decisions. Don't store one-time debugging notes.
- **Keep MEMORY.md under 200 lines.** Lines beyond that get truncated anyway.

### What to Put in Memory

- Your role and expertise level (so Claude calibrates its explanations)
- Project-specific context that isn't obvious from the code
- Workflow preferences and feedback ("don't do X", "always do Y")
- Credentials locations and API configurations (never the actual secrets)

### What NOT to Put in Memory

- Code patterns or architecture (Claude can read the code)
- Git history (Claude can run git log)
- Debugging solutions (the fix is in the code)
- Anything already in CLAUDE.md

### CLAUDE.md and Path Files — Giving Claude a Map of Your Project

Claude can read any file in your project, but it doesn't automatically know *where* things are or *how* your project is organized. You can fix this with two tools:

#### CLAUDE.md — Project Instructions

`CLAUDE.md` lives in your project root and acts as a permanent instruction set for Claude. Every conversation loads it automatically. Use it to tell Claude:

- Your project's tech stack and conventions
- Rules Claude should always follow ("always use TypeScript", "never modify the database schema directly")
- Where important things live ("API routes are in `src/routes/`", "tests are in `__tests__/`")
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
- prisma/schema.prisma — Database schema

## Rules
- All new API routes must have corresponding tests
- Use snake_case for database columns, camelCase for TypeScript
```

#### Path Files — Workshop Shortcuts

For larger projects, you can create **path files** — small reference documents that tell Claude where to find things it needs to work on. Think of them as a table of contents for your codebase.

This is especially useful when you want Claude to **workshop or iterate on specific parts** of your project. Instead of Claude searching through hundreds of files, you point it directly at what matters:

```markdown
# paths.md (or include in CLAUDE.md)

## Key Files for Feature Work
- src/auth/login.ts — Login flow, JWT token generation
- src/auth/middleware.ts — Auth middleware for protected routes
- src/db/schema.prisma — Database schema (source of truth)
- src/api/users.ts — User CRUD endpoints
- src/components/Dashboard.tsx — Main dashboard UI
- .env.example — Required environment variables
```

When you start a session, you can tell Claude: "Read paths.md first, then work on the login flow." This saves context window space (Claude doesn't need to explore) and ensures it's looking at the right files.

---

## 4. Writing Better Prompts — Be Clear, Detailed, and Explicit

### The Mental Model

Think of Claude as a **brilliant but literal-minded assistant** — incredibly capable when given clear instructions, but prone to going off-track with vague ones. Claude won't fill in gaps the way a human colleague might. If you leave something ambiguous, Claude will make assumptions and those assumptions may not match what you wanted.

### The Key Principles

1. **Be specific about what you want.** "Make it better" gives you random changes. "Add input validation to the email field that checks for @ and a domain" gives you exactly what you need.

2. **State your constraints.** "Don't modify any other files." "Keep the existing API contract." "Use the existing database schema."

3. **Describe the end state.** Tell Claude what "done" looks like. "When this is complete, a user should be able to click the button and see their dashboard update in real-time."

4. **Break complex asks into steps.** Don't dump a 500-word feature request in one message. Break it into logical pieces.

### For Smaller Projects / Quick Asks

**Write your prompt in a separate document first** (Word, Notes, whatever), then copy-paste it into the terminal. This forces you to think through what you actually want before burning tokens on a half-baked prompt.

Benefits:
- You can edit and refine before sending
- You avoid the "oh wait, I also need..." follow-up messages that eat context
- You can reuse good prompts as templates

### For Larger Projects (Ramiro's Method)

**Create a series of separate feature documents — aim for 9-10 documents that each explain one feature you want built.** Each document should clearly describe:
- What the feature does
- How it should behave
- What the acceptance criteria are
- Any constraints or edge cases

For a typical project, you might have documents like:
1. `user-authentication.md` — Login, signup, password reset
2. `dashboard.md` — Main user dashboard layout and data
3. `notifications.md` — Email and in-app notification system
4. `settings.md` — User preferences and account management
5. `api-integration.md` — Third-party API connections
6. `search.md` — Search functionality and filters
7. `payments.md` — Billing and subscription handling
8. `admin-panel.md` — Admin tools and user management
9. `analytics.md` — Usage tracking and reporting
10. `deployment.md` — CI/CD, hosting, environment setup

This is formalized in this repo as the **FRED (Feature Requirement Document)** system — see `CLAUDE.md` for the template.

Why this works:
- Forces you to think through the feature before building
- Gives Claude a complete spec to work from (fewer misunderstandings)
- Creates documentation as a side effect
- Makes it easy to hand off features to different conversation windows
- Each document maps to one terminal window (see Section 5)

---

## 5. Terminal Window Management (Jarrett's Method)

### One Terminal Window Per Feature

Every time you start working on something new — a new feature, a new bug, a new question — **open a fresh terminal window.** Don't keep asking Claude new things in the same window.

### Why This Works

- **Fresh context for each task.** Claude isn't trying to hold your auth system in memory while you ask about CSS styling.
- **Naturally stays under the 30-40% threshold.** Each window handles one focused task, so you rarely hit the context limit.
- **Easier to go back.** If you need to revisit something, the conversation history for that specific feature is isolated and easy to find.
- **Parallel work.** You can have Claude working on one feature in one window while you review another.

### Practical Workflow

1. Open Terminal Window A → "Build the login form"
2. Open Terminal Window B → "Set up the database schema"
3. Open Terminal Window C → "Write tests for the API"
4. Each window stays focused and efficient

### When to Start a New Window

- New feature or task
- Context is at 30-40%
- Claude seems confused or is forgetting earlier instructions
- You're switching from one area of the codebase to another

---

## 6. IDE vs CLI — Choosing Your Interface

Claude is available in two main forms: the **CLI (Command Line Interface)** and **IDE extensions** (VS Code, JetBrains, etc.). Each has strengths.

### CLI (Terminal)

**Best for:** Power users, full control, complex multi-step tasks

| Pros | Cons |
|------|------|
| Full terminal access — Claude can run any command | No visual file browser |
| Multiple windows for parallel work | Steeper learning curve |
| Direct file system access | No inline code highlighting |
| Memory and CLAUDE.md system | Text-only interface |
| Works over SSH / remote machines | |

**Use the CLI when:**
- You're building features from scratch
- You need Claude to run tests, deploy, or manage git
- You want maximum control over context and memory
- You're working on backend / infrastructure tasks

### IDE Extensions (VS Code, Cursor, etc.)

**Best for:** Visual learners, front-end work, code review

| Pros | Cons |
|------|------|
| See code changes inline | Less control over context |
| Visual diff view | May not have full terminal access |
| Click to navigate files | Memory system may differ |
| Syntax highlighting in context | IDE-specific quirks |
| Good for front-end / UI work | |

**Use the IDE when:**
- You're doing front-end work and want to see changes visually
- You're reviewing or refactoring existing code
- You prefer a GUI over the terminal
- You're new to Claude and want a gentler learning curve

### Recommendation

**Start with the CLI** to understand how Claude really works — context, memory, tokens, and all. Once you're comfortable, add the IDE extension for visual tasks. Many power users use both: CLI for building, IDE for reviewing.

---

## 7. Token Optimization — Maximizing Your Daily Usage

### How the Token System Works

Claude's usage limits operate on a **rolling 5-hour window.** Your tokens don't reset at midnight — they reset 5 hours after you started using them.

### Checking Your Token Usage

Use `/usage` in Claude Code to see your current token consumption and when your next reset happens. **[TODO: Add screenshots showing the token usage display and reset timer here]**

### The Math

| Strategy | Windows | Effective Output |
|----------|---------|-----------------|
| Casual (noon–5pm) | 1 cycle | 1x tokens |
| Early start (7am–5pm) | 2 cycles | 2x tokens |
| Full day (7am–10pm) | 3 cycles | 3x tokens |

### How to Get 2x Tokens

1. **Start early.** If you begin at 7:00 AM, your first window runs 7am–12pm.
2. Your tokens reset at 12:00 PM and you get a full second window from 12pm–5pm.
3. That's **double the output** compared to someone who starts at noon.

### How to Get 3x Tokens

1. Start at 7:00 AM → first window resets at 12:00 PM
2. Second window 12:00 PM → resets at 5:00 PM
3. Third window 5:00 PM → resets at 10:00 PM
4. That's **15 hours and 3 full cycles** of tokens.

### The Early Start Trick

Even if you're not ready to do real work at 7am, you can **kick off a planning task** to start the clock:

> "Review the codebase and make a plan for what to accomplish today."

This starts your 5-hour timer. By the time you're actually in flow at 9 or 10am, you've already used some of window 1, and window 2 is that much closer to being available.

### Key Insight

The difference between a casual user and an optimized user isn't skill — it's scheduling. Plan your heavy coding sessions to align with fresh token windows.

---

## 8. Claude Model Modes — Haiku, Sonnet, and Opus

Claude isn't one model — it's a family of models with different speed/capability tradeoffs. You can switch between them in Claude Code using the `/model` command or keyboard shortcuts.

### The Three Models

| Model | Speed | Capability | Cost (Tokens) | Best For |
|-------|-------|-----------|---------------|----------|
| **Haiku** | Fastest | Good | Lowest | Quick questions, simple edits, boilerplate |
| **Sonnet** | Fast | Great | Medium | Most coding tasks, debugging, features |
| **Opus** | Slower | Best | Highest | Complex architecture, difficult bugs, nuanced reasoning |

### When to Use Each

#### Haiku (Fast Mode)
- "What does this function do?"
- "Rename this variable across the file"
- "Add a comment to this function"
- Simple, mechanical tasks where speed matters more than depth
- Toggle with `/fast` in Claude Code

#### Sonnet (Default)
- Building features from a FRED document
- Debugging most issues
- Writing tests
- Code review and refactoring
- This is your **daily driver** — it handles 80% of tasks well

#### Opus (Heavy Lifting)
- Complex multi-file architectural changes
- Debugging subtle, hard-to-reproduce issues
- Tasks requiring deep reasoning across many files
- When Sonnet gives you a wrong answer and you need more horsepower
- Planning and designing system architecture

### Switching Models

In Claude Code:
- `/model` — select a model interactively
- `/model opus` — switch directly to Opus
- `/model sonnet` — switch directly to Sonnet
- `/model haiku` — switch directly to Haiku

### The Strategy

**Start with Sonnet.** If the task is trivial, drop to Haiku to save tokens. If Sonnet isn't getting it right or the problem is genuinely complex, escalate to Opus. Think of it like gears:

- **Haiku** = 1st gear — quick acceleration, simple tasks
- **Sonnet** = 3rd gear — cruising speed, everyday work
- **Opus** = 5th gear — maximum power, complex problems

### Pro Tip

Using Haiku for simple tasks conserves your token budget, leaving more room for Opus when you really need it. Don't burn Opus tokens on "add a CSS class" — that's a Haiku job.

---

## Putting It All Together

Here's the optimized daily workflow combining all eight topics:

### Morning (Window 1)
1. Start Claude early — even just a planning prompt to start the timer
2. Open a fresh terminal window for each task
3. Write prompts in a doc before pasting them in
4. Commit and push frequently

### Midday (Window 2)
5. Tokens have reset — start your heavy feature work
6. Use FREDs for complex features
7. Keep memory files lean — prune anything stale
8. Clear context at 30-40% or when switching tasks

### Evening (Window 3, if needed)
9. Third token window for testing, polish, or new features
10. Save any important context to memory before ending the day

---

## Quick Reference Card

| Principle | Rule of Thumb |
|-----------|--------------|
| From ChatGPT | Claude works in your real codebase — commit often |
| Context window | Clear at 30-40% usage |
| Memory files | Keep MEMORY.md under 200 lines |
| Prompt quality | Write in a doc first, be explicit |
| Feature scope | 9-10 FREDs, one per feature |
| Terminal windows | One window per task |
| IDE vs CLI | CLI for building, IDE for reviewing |
| Token windows | 5-hour rolling reset, start early |
| Model modes | Haiku=quick, Sonnet=daily, Opus=complex |
| Commits | Small, frequent, always push |
