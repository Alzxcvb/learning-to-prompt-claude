# Claude Tips & Tricks — Presentation Summary

A practical guide to prompting Claude effectively and maximizing your Claude Code subscription for vibe coding and software development.

---

## 1. Understanding the Context Window

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

---

## 2. Memory Files — Making Claude Remember (Without Wasting Context)

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

---

## 3. Writing Better Prompts — Be Clear, Detailed, and Explicit

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

**Create separate feature documents for each feature you want built.** Each document should clearly describe:
- What the feature does
- How it should behave
- What the acceptance criteria are
- Any constraints or edge cases

This is formalized in this repo as the **FRED (Feature Requirement Document)** system — see `CLAUDE.md` for the template.

Why this works:
- Forces you to think through the feature before building
- Gives Claude a complete spec to work from (fewer misunderstandings)
- Creates documentation as a side effect
- Makes it easy to hand off features to different conversation windows

---

## 4. Terminal Window Management (Jarrett's Method)

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

## 5. Token Optimization — Maximizing Your Daily Usage

### How the Token System Works

Claude's usage limits operate on a **rolling 5-hour window.** Your tokens don't reset at midnight — they reset 5 hours after you started using them.

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

## Putting It All Together

Here's the optimized daily workflow combining all five tips:

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
| Context window | Clear at 30-40% usage |
| Memory files | Keep MEMORY.md under 200 lines |
| Prompt quality | Write in a doc first, be explicit |
| Feature scope | One FRED per feature |
| Terminal windows | One window per task |
| Token windows | 5-hour rolling reset, start early |
| Commits | Small, frequent, always push |
