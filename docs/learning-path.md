# Suggested Learning Path

A step-by-step order for learning Claude Code prompting and vibe coding, from absolute beginner to optimized power user.

---

## Level 1: Getting Started (Day 1)

### 1.1 — Install and Run Claude Code
- Install Claude Code CLI
- Open a terminal and start your first conversation
- Try a simple ask: "Explain what this file does" on any code file

### 1.2 — Learn the Basic Commands
- `/help` — see available commands
- `/usage` — check your context and token usage
- `/clear` — reset your conversation context
- Up/down arrows — navigate command history

### 1.3 — Understand What the Context Window Is
- **Read:** Presentation Summary, Section 1
- **Exercise:** Start a conversation, ask 10-15 questions, then check `/usage`. Notice how it grows.
- **Key takeaway:** Everything you say and everything Claude reads counts toward the limit.

---

## Level 2: Writing Good Prompts (Day 2-3)

### 2.1 — The "Write It First" Method
- **Read:** Presentation Summary, Section 3
- **Exercise:** Pick a small task (e.g., "add a footer to my webpage"). Write the full prompt in a text editor first. Include: what you want, where it goes, what it should look like, and any constraints.
- **Key takeaway:** Time spent writing a clear prompt saves 5x the time you'd spend on follow-up corrections.

### 2.2 — Practice Being Explicit
- **Bad prompt:** "Make the button look better"
- **Good prompt:** "Change the submit button to have a blue (#2563EB) background, white text, rounded corners (8px), and a hover effect that darkens the background by 10%. Keep the same size and position."
- **Exercise:** Take 3 vague prompts and rewrite them to be specific. Test both versions and compare results.

### 2.3 — Learn to Give Constraints
- Practice adding boundaries: "Don't change any other files", "Use only CSS, no JavaScript", "Keep the existing function signature"
- **Key takeaway:** Constraints prevent Claude from "helping" in ways you didn't ask for.

---

## Level 3: Context Management (Day 4-5)

### 3.1 — The 30-40% Rule
- **Read:** Presentation Summary, Section 1
- **Exercise:** Work on a task and monitor `/usage`. When you hit 30%, clear context and continue. Notice how Claude's responses improve with fresh context.

### 3.2 — One Window Per Task
- **Read:** Presentation Summary, Section 4
- **Exercise:** Work on two separate tasks. Use a different terminal window for each. Compare this to doing both in one window.
- **Key takeaway:** Focused conversations produce better results than long, meandering ones.

### 3.3 — When to Clear vs. When to Continue
- **Clear when:** switching tasks, at 30-40% usage, Claude seems confused, you're starting something unrelated
- **Continue when:** you're iterating on the same piece of code, Claude needs the conversation history to understand your changes

---

## Level 4: Memory and Persistence (Day 6-7)

### 4.1 — Set Up Your Memory File
- **Read:** Presentation Summary, Section 2
- **Exercise:** Tell Claude about yourself — your role, experience level, and preferences. Check that it saved to memory. Start a new conversation and verify Claude remembers.

### 4.2 — Learn What to Store vs. What to Skip
- **Store:** your preferences, project context, repeated feedback
- **Skip:** code patterns, git history, one-time fixes
- **Exercise:** Review your memory files after a week. Delete anything that's stale or that Claude can figure out from the code.

### 4.3 — Set Up CLAUDE.md for Your Project
- CLAUDE.md lives in your project root and gives Claude project-specific instructions
- **Exercise:** Create a CLAUDE.md with your project's key conventions, tech stack, and any rules Claude should follow.

---

## Level 5: Project Organization (Week 2)

### 5.1 — Feature Requirement Documents (FREDs)
- **Read:** Presentation Summary, Section 3 (Ramiro's Method) + CLAUDE.md FRED template
- **Exercise:** Pick a feature you want to build. Write a complete FRED before asking Claude to implement anything.
- **Key takeaway:** 20 minutes of planning saves hours of back-and-forth.

### 5.2 — Multi-Window Workflow
- **Read:** Presentation Summary, Section 4 (Jarrett's Method)
- **Exercise:** Plan a small project with 3 features. Build each in its own terminal window. Practice the commit-and-push rhythm.

### 5.3 — Commit Discipline
- Small, frequent commits after each logical piece
- Always push — don't just commit locally
- Write clear commit messages that explain why, not just what

---

## Level 6: Token Optimization (Week 2-3)

### 6.1 — Understand the 5-Hour Rolling Window
- **Read:** Presentation Summary, Section 5
- **Exercise:** Track when you start using Claude and when you hit limits. Map your actual usage windows.

### 6.2 — Plan Your Day Around Token Resets
- **Exercise:** Try the "early start" strategy. Begin with a planning prompt at 7am, do real work by 9am, and notice that your tokens reset by noon.
- **Key takeaway:** 2x or 3x tokens isn't about paying more — it's about starting earlier.

### 6.3 — Combine Everything
- Start early (token optimization)
- Plan with FREDs (prompt quality)
- One window per feature (context management)
- Clear at 30-40% (context window)
- Lean memory files (persistence without bloat)
- Commit frequently (progress checkpoints)

---

## Ongoing Practice

### Weekly Review
- Prune your memory files — remove stale entries
- Review your FREDs — are they detailed enough?
- Check your workflow — are you clearing context early enough?

### Common Mistakes to Avoid
1. **Vague prompts** — "make it work" wastes tokens on guesswork
2. **Overloaded context** — pushing past 40% degrades quality
3. **Bloated memory** — 500 lines of memory = less room for code
4. **One mega-window** — doing everything in one conversation
5. **Ignoring token scheduling** — starting late and hitting limits by 3pm
6. **Not committing** — losing work when context clears or sessions end

---

## Resources

- [Presentation Summary](presentation-summary.md) — Full guide with all tips
- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Anthropic Prompt Engineering Guide](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering)
