# Ralph Loop Skill

A reusable skill for maintaining context continuity across Claude Code sessions.

---

## What This Solves

LLMs degrade as context grows (past ~100K tokens). Long sessions drift, forget context, and produce worse output. The Ralph Loop pattern solves this by:

1. Persisting all critical state to external files
2. Starting each session fresh (full cognitive capacity)
3. Reading accumulated knowledge from files, not conversation history

**Key principle:** Fresh brain + accumulated knowledge.

---

## Quick Setup (3 steps)

### 1. Create a session-state file

Add this file to your project (adjust path as needed):

```markdown
# Session State

**READ THIS FILE FIRST when starting any session.**

## Status

- **Status:** idle
- **Last updated:** [date]
- **Current task:** [description]

---

## If Resuming Mid-Task

When status is "in_progress", restore context from below.

### Position
- **Phase:** [current phase of work]
- **Current step:** [what step we're on]
- **Pending action:** [exact next thing to do]

### Context
- **What's been done:** [list of completed items]
- **What's left:** [remaining items]
- **Blockers/issues:** [any problems encountered]

### Key Decisions Made
[Important choices that shouldn't be re-decided]

### Handoff Notes
[Anything a fresh session needs to know to continue seamlessly]

---

## Resume Instructions

1. Read this file first
2. If status is "in_progress": Continue from Position
3. If status is "idle": Start new task normally
4. Update this file at every significant checkpoint
```

### 2. Add to your CLAUDE.md

Add this section to your project's CLAUDE.md:

```markdown
## Context Management (Ralph Loop)

This project uses external state files for session continuity. Each conversation may be a fresh context window, so all critical state must be persisted to files.

**Key principle:** Fresh brain + accumulated knowledge. Never rely on conversation history for critical state.

### Before starting any task:
1. Read `session-state.md` first
2. If status is "in_progress", resume from the recorded position
3. If status is "idle", proceed normally

### During work:
1. Update session-state.md at every significant checkpoint
2. Log what's been done, what's left, and any key decisions
3. Include the exact next action so a fresh session can continue

### When finishing:
1. Set status to "idle"
2. Clear the mid-task fields
3. Note what was accomplished
```

### 3. Use the checkpoint pattern

During work, update your session-state file:
- Before any multi-step operation
- After completing significant milestones
- When making decisions that shouldn't be revisited
- Before any operation that might take a long time

---

## Checkpoint Template

Use this format when updating session-state.md mid-task:

```markdown
## Status

- **Status:** in_progress
- **Last updated:** 2026-02-04 14:30
- **Current task:** Implementing user authentication

---

## If Resuming Mid-Task

### Position
- **Phase:** Implementation
- **Current step:** Step 3 of 5 - Adding JWT validation middleware
- **Pending action:** Create validateToken function in auth/middleware.js

### Context
- **What's been done:**
  - Created User model with password hashing
  - Added /register endpoint
  - Added /login endpoint that returns JWT
- **What's left:**
  - JWT validation middleware
  - Protected route example
  - Tests
- **Blockers/issues:** None

### Key Decisions Made
- Using bcrypt for password hashing (cost factor 12)
- JWT expires in 24 hours
- Refresh tokens not implemented (keeping simple for v1)

### Handoff Notes
The login endpoint is working. Test with:
curl -X POST http://localhost:3000/login -d '{"email":"test@test.com","password":"test123"}'
```

---

## For Complex Projects

For projects with multiple workstreams, use multiple state files:

```
project/
├── session-state.md           # Overall project state
├── states/
│   ├── feature-auth.md        # Auth feature state
│   ├── feature-payments.md    # Payments feature state
│   └── bugfix-123.md          # Specific bug state
```

Or use a single file with sections:

```markdown
# Session State

## Active Workstreams

### Authentication (in_progress)
- Current: Adding JWT middleware
- Next: validateToken function

### Payments (idle)
- Completed: Stripe integration
- Next: Webhook handlers

### Bug #123 (blocked)
- Issue: Cannot reproduce
- Blocked on: Need production logs
```

---

## Invoking This Skill

When you want to use Ralph Loop in a conversation, say:

> "Let's use Ralph Loop for this task"

Or:

> "Checkpoint the current state"

Or:

> "Set up Ralph Loop for this project"

The assistant should then:
1. Create or read the session-state file
2. Follow the checkpoint pattern throughout the work
3. Keep the state file updated at every significant point

---

## Why "Ralph Loop"?

Named after Ralph Wiggum from The Simpsons - "lovably persistent." The pattern has an AI attempt tasks repeatedly with fresh context until success, learning from each attempt via external state files.

The key insight: The official "Ralph Loop" plugins that just retry in the same context window miss the point. The real power comes from **fresh context + accumulated knowledge**.

---

## Credits

Pattern popularized by Chase H AI. This skill adapted for general Claude Code use.

Learn more: https://theslowai.substack.com/
