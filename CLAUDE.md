# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

This repository is newly initialized and contains no source code yet. Update this file as the project structure and tooling are established.

After adding a new feature you will document it every single time, no exceptions.

---

## Feature Requirement Document (FRED) Rule

### When to Apply

Apply when the user requests implementation of a **new feature or new functionality**:

- Requests to implement, add, create, or build new features
- Requests for new functionality that doesn't exist yet
- Requests to update a document in `docs/features/`

**Do NOT apply for:** bug fixes, code reviews, explanations, or modifications to existing features.

### Process

1. **Generate a FRED first** — before any implementation work.
2. Save the FRED in `docs/features/` using kebab-case filename (e.g., `user-authentication.md`).
3. **Present the FRED to the user for review** and wait for approval before implementing.
4. Only skip if the user explicitly says "skip FRED" or "implement directly".

### FRED Template Sections

- **Feature Name**: Short, descriptive title.
- **Goal**: What problem does this solve and why does it exist?
- **User Story**: As a [user type], I want to [goal], so that I can [benefit].
- **Functional Requirements**: Core behaviors the feature must support — specific and measurable.
- **Data Requirements** *(optional)*: New tables, fields, relationships, or reused existing data.
- **User Flow**: Step-by-step actions the user performs from start to finish.
- **Acceptance Criteria**: Clear, verifiable conditions defining "done".
- **Edge Cases**: Tricky or error scenarios the system must handle.
- **Non-Functional Requirements** *(optional)*: Performance, security, UX constraints.

### Trigger Phrases (Apply Rule)

"Implement X", "Add X", "Create X", "Build X", "I need X", "Let's add X", or any request implying new functionality.

### Non-Trigger Phrases (Do NOT Apply)

"Fix X", "Debug X", "Update existing X", "How does X work?", or any request about existing functionality.