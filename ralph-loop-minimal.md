# Ralph Loop - Minimal Drop-in

Copy these two pieces into any project.

---

## 1. Add to CLAUDE.md

```markdown
## Context Management (Ralph Loop)

Each conversation may be a fresh context window. Persist all critical state to files.

**Principle:** Fresh brain + accumulated knowledge.

### Workflow:
1. **Start of session:** Read `session-state.md` first. If status is "in_progress", resume from recorded position.
2. **During work:** Update session-state.md at every checkpoint (phase changes, key decisions, before long operations).
3. **End of task:** Set status to "idle", note what was done.

### session-state.md fields:
- Status (idle/in_progress)
- Current task and phase
- What's done, what's left
- Pending action (exact next step)
- Key decisions made
- Handoff notes for fresh session
```

---

## 2. Create session-state.md

```markdown
# Session State

**Read this first.**

## Status
- **Status:** idle
- **Last updated:** [date]
- **Task:** [current or last task]

---

## Mid-Task State (when in_progress)

### Position
- **Phase:** [phase]
- **Step:** [current step]
- **Next action:** [exact next thing to do]

### Progress
- **Done:** [completed items]
- **Remaining:** [items left]
- **Blockers:** [issues]

### Decisions
[Key choices made - don't re-decide these]

### Handoff
[What a fresh session needs to know]
```

---

## Usage

**To checkpoint:** Update session-state.md with current position and set status to "in_progress"

**To resume:** Read session-state.md, continue from Next Action

**To complete:** Set status to "idle", clear mid-task fields

That's it. Fresh brain, accumulated knowledge.
