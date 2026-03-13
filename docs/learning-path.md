# Suggested Learning Path

A step-by-step order for learning Claude Code prompting and vibe coding, from absolute beginner to optimized power user.

---

## Level 1: Getting Started (Day 1)

### 1.1 — Transitioning from ChatGPT / Other Platforms
- **Read:** Presentation Summary, Section 1
- Understand the key differences: Claude works in your real codebase, not a sandbox
- You don't paste code — Claude reads your files directly
- **Exercise:** If you've used ChatGPT for coding, try the same task in Claude Code and notice the difference.

### 1.2 — Migrate Your Memories (Do This First!)
- **Read:** Presentation Summary, Section 1 — "Migrating Your Memory"
- **Exercise:** Before you start using Claude, extract your memories from ChatGPT or your current platform:
  1. Ask your current AI: "List every memory you have about me"
  2. Follow up: "What else do you need to fully capture everything?"
  3. Download your memories from the platform settings
  4. Combine into a master memory document
  5. Feed the master doc to Claude on your first session
- **Key takeaway:** Your AI context is portable. Don't start from zero — bring everything with you.

### 1.3 — Install and Run Claude Code
- Install Claude Code CLI
- Open a terminal and start your first conversation
- Try a simple ask: "Explain what this file does" on any code file

### 1.4 — Learn the Basic Commands
- `/help` — see available commands
- `/usage` — check your context and token usage
- `/clear` — reset your conversation context
- `/model` — switch between Haiku, Sonnet, and Opus
- Up/down arrows — navigate command history

### 1.5 — Understand What the Context Window Is
- **Read:** Presentation Summary, Section 2
- **Exercise:** Start a conversation, ask 10-15 questions, then check `/usage`. Notice how it grows.
- **Key takeaway:** Everything you say and everything Claude reads counts toward the limit.

---

## Level 2: Writing Good Prompts (Day 2-3)

### 2.1 — The "Write It First" Method
- **Read:** Presentation Summary, Section 4
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
- **Read:** Presentation Summary, Section 2
- **Exercise:** Work on a task and monitor `/usage`. When you hit 30%, clear context and continue. Notice how Claude's responses improve with fresh context.

### 3.2 — One Window Per Task
- **Read:** Presentation Summary, Section 5
- **Exercise:** Work on two separate tasks. Use a different terminal window for each. Compare this to doing both in one window.
- **Key takeaway:** Focused conversations produce better results than long, meandering ones.

### 3.3 — When to Clear vs. When to Continue
- **Clear when:** switching tasks, at 30-40% usage, Claude seems confused, you're starting something unrelated
- **Continue when:** you're iterating on the same piece of code, Claude needs the conversation history to understand your changes

---

## Level 4: Memory and Persistence (Day 6-7)

### 4.1 — Set Up Your Memory File
- **Read:** Presentation Summary, Section 3
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
- **Read:** Presentation Summary, Section 4 (Ramiro's Method) + CLAUDE.md FRED template
- **Exercise:** Pick a feature you want to build. Write a complete FRED before asking Claude to implement anything.
- **Key takeaway:** 20 minutes of planning saves hours of back-and-forth.

### 5.2 — Multi-Window Workflow
- **Read:** Presentation Summary, Section 5 (Jarrett's Method)
- **Exercise:** Plan a small project with 3 features. Build each in its own terminal window. Practice the commit-and-push rhythm.

### 5.3 — Commit Discipline
- Small, frequent commits after each logical piece
- Always push — don't just commit locally
- Write clear commit messages that explain why, not just what

---

## Level 6: IDE vs CLI & Model Modes (Week 2)

### 6.1 — Try Both Interfaces
- **Read:** Presentation Summary, Section 6
- **Exercise:** Do the same task in both CLI and IDE. Build a function in the terminal, then refactor it using the VS Code extension. Notice the strengths of each.
- **Key takeaway:** CLI for building and full control, IDE for visual review and front-end work.

### 6.2 — Learn the Model Modes
- **Read:** Presentation Summary, Section 8
- **Exercise:** Take a simple task and run it on Haiku (`/model haiku`). Then take a complex debugging task and use Opus (`/model opus`). Compare the quality and speed.
- **Key takeaway:** Use Haiku for quick/simple, Sonnet for everyday, Opus for hard problems. Switching models saves tokens.

### 6.3 — Develop Your Model Strategy
- Start every session on Sonnet (default)
- Drop to Haiku for boilerplate, renaming, simple questions
- Escalate to Opus when Sonnet fails or the task is genuinely complex
- **Exercise:** Track which model you use for a full day. Were there tasks where you used Opus but Haiku would have been fine?

---

## Level 7: Token Optimization (Week 2-3)

### 7.1 — Understand the 5-Hour Rolling Window
- **Read:** Presentation Summary, Section 7
- **Exercise:** Track when you start using Claude and when you hit limits. Map your actual usage windows.

### 7.2 — Plan Your Day Around Token Resets
- **Exercise:** Try the "early start" strategy. Begin with a planning prompt at 7am, do real work by 9am, and notice that your tokens reset by noon.
- **Key takeaway:** 2x or 3x tokens isn't about paying more — it's about starting earlier.

### 7.3 — Combine Everything
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
7. **Using Opus for everything** — burns tokens fast on tasks Haiku could handle
8. **Treating Claude like ChatGPT** — pasting code instead of letting Claude read files directly

---

## Resources

- [Presentation Summary](presentation-summary.md) — Full guide with all tips
- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Anthropic Prompt Engineering Guide](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering)
