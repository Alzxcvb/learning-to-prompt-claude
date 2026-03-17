# Claude Tips, Tricks & Autonomous Agents — Cheat Sheet

By Alex Coffman & Tom Nguyen

---

## Migrating from Other Platforms

**Download from settings:**
- ChatGPT: Settings → Personalization → Memory → Manage Memory (also Settings → Data Controls → Export Data)
- Gemini: Settings → Extensions & Activity
- Copilot: Microsoft account settings

**Ask your current AI:** "List every memory you have about me"
**Follow up:** "What else do you need to fully capture everything?"
**Ask Claude:** "What should I ask [OTHER PLATFORM] to fully transfer the entirety of its knowledge about me to you?"

---

## What Is GitHub?

Google Drive for code. Use it to share and collaborate on code.

Download this lesson plan: **https://github.com/Alzxcvb/learning-to-prompt-claude**

Green "Code" button → "Download ZIP"

---

## What Can I Actually Build?

- A website
- A personalized workout plan
- A bot that gives you a daily news report
- A research deep-dive for a book, thesis, or blog
- A personalized nutrition plan

**Pick ONE thing. Don't plan for 3 hours. Build for 30 minutes.**

---

## Memory Files & Project Configuration

- Memory stores a 1-line explanation and reference to a memory file that will be reviewed fully if relevant
- **Keep MEMORY.md under 200 lines** and prune regularly
- More memory = less room for work
- **CLAUDE.md** = permanent project instructions (lives in your project folder)
- **Pathname files** = point Claude at the right files

**Finding a file path on Mac:** Right-click file in Finder → hold Option → "Copy as Pathname"

---

## Understanding the Context Window

- **The 30-40% rule** — clear context before it degrades
- **Context pollution** — mistakes stick around, correcting ≠ erasing
- **Bypass context limitations:** ask Claude to call up other Agents/sub-agents to do work (like searching the web), which will use up a ton of tokens and fill up context fast
- **Recovery options:** Full clear vs triple escape + retcon

### Retcon (Tom's Recommendation)

1. Hit Escape 3 times
2. Select where you want to rewind the conversation to

---

## Slash Commands

| Command | What It Does |
|---------|-------------|
| `/help` | See available commands |
| `/usage` | Check your context and token usage |
| `/clear` | Nuke conversation entirely, reloads from memory |
| `/compact` | Truncate conversation but keep the essence of the convo |
| `/model` | Switch between Haiku, Sonnet, and Opus |
| `!` + command | Run terminal commands without leaving Claude (e.g., `! git status`) |
| `Escape` x3 | Cancel/interrupt current response |
| Up/Down arrows | Navigate command history |

---

## Writing Better Prompts

- Be specific, state constraints, describe the end state. Maximize clarity + details.
- Claude is the name of a 16-year-old retrograde amnesiac autistic savant...
- **Write prompts in a Word doc first**, then paste in
- For larger projects: **9-10 feature documents** (Ramiro's method / FREDs). For example: "Add a footer" or "Change the submit button"

---

## Terminal Window Management (from Jarrett)

- One window per feature/task
- Fresh context, parallel work, keep the context usage under 30-40%
- Check your CLI now using `/context` command — how much are you using?

---

## CLI vs IDE

| CLI | IDE |
|-----|-----|
| Full control, building, backend | Visual, front-end, code review |

**IDE options:** VS Code, Antigravity, Cursor

**Recommendation:** Start with CLI, add IDE later because it can be more overwhelming and it's already a lot for new folks.

---

## Claude Model Modes

| Model | Role |
|-------|------|
| **Haiku** | Fast/cheap |
| **Sonnet** | Daily driver |
| **Opus** | Heavy lifting |

**Gear analogy:** Haiku = 1st gear, Sonnet = 2nd gear, Opus = 3rd gear

Switch with `/model` command.

---

## Token Optimization

- Tokens reset on a **rolling 5-hour window** (not midnight)

| Start Time | Windows | Output |
|-----------|---------|--------|
| Noon | 1 cycle (noon–5pm) | 1x |
| 7am | 2 cycles (7am–noon, noon–5pm) | 2x |
| 7am + evening | 3 cycles (7am–noon, noon–5pm, 5pm–10pm) | 3x |

**Early start trick:** Kick off a planning prompt to start the clock.
