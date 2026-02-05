# App Development Feedback

Collected from sessions to improve the app.

---

## Session 1 - 2026-02-04 (Testing/Prototyping)

### What Worked
- Speaking via Wispr Flow transcription
- Listening via macOS text-to-speech (Thomas voice)
- One question at a time approach
- "What did you mean?" teaching method
- Short grammar explanations with "want more?" option
- Active wrap-up (hear then repeat your text)
- Read+Write and Listen+Speak conversation modes
- Reality check during onboarding

### What Needs Work
- Listening exercises: text visible in Claude Code tool calls (need to hide in real app)
- Accent input: keyboard shortcuts don't work in Claude Code terminal
- Long passage repetition tests memory, not language - keep sentences short
- Assessment questions were too leading/predictable
- Recognition ≠ production - need to test both

### Design Decisions Confirmed
- No gamification (no streaks, points, badges)
- Calm, clean aesthetic (Slow AI branding)
- Always show grammar explanation, offer deeper dive
- Accept unaccented input, show corrected version
- Track four skills separately, weight toward weakest
- Adaptive + task-based progression
- Teach "I don't understand" phrases early
- First week is also assessment - adjust level based on actual performance

### Feature Requests
- Accent palette or auto-correct for typing
- Playback controls for listening (again, slower)
- Scaffolded help when stuck (replay → slower → reveal)
- Track common errors for focused practice
- Accept prior knowledge from other sources (Duolingo, etc.)

---

## Questions to Ask Periodically

At end of sessions, occasionally ask:
1. "How was that session?"
2. "What felt confusing?"
3. "What would you like more or less of?"
4. "Any other feedback?"

Log responses here.

---

## Session 2 - 2026-02-04 (First Real Session)

### How was it?
Really good, perhaps a little short.

### Suggestions
1. **Track active time, not elapsed time** - Users may start/stop. Track actual learning time (questions answered).
2. **Offer extension if short** - If committed to 30-min session but under 20 mins done, offer to continue.
3. **Warn on time limit** - When approaching end of session, tell user and ask if they want to continue.

### Feature Request: Ralph Loop Implementation
Implement mid-session checkpointing so a fresh context window can resume exactly where user left off. Store:
- Exact current position (phase, exercise, pending question)
- Unsaved progress (words introduced, errors made)
- Conversation context

**Status:** Implemented - added `session-state.md` and checkpointing instructions to CLAUDE.md.

### Pacing Concern
User notes tendency to rush through material.

**Rule added:**
- 1-2 sessions/day: Fine
- 3+ sessions/day: Require retention quiz (5 questions from earlier sessions) before allowing more. If <60%, suggest break. If ≥60%, allow but keep session lighter.

**Status:** Implemented in CLAUDE.md and session-state.md tracks sessions per day.

### Listening Practice (Session 2)
Not enough listening. Two changes needed:
1. **Play audio for all new phrases** when introducing them (don't just show text)
2. **More listening exercises overall** throughout sessions

**Status:** Added to CLAUDE.md

### Tool Output Clutter (Session 2)
Seeing file operations mid-session is distracting from learning.

**Solution:** Batch all file operations to wrap-up phase. During the lesson, only show French content. Save everything at the end in one block.

**Trade-off:** If session interrupted, progress not saved until wrap-up. Acceptable for 30-min sessions.

**Status:** Updated approach for future sessions

---

## Session 3 - 2026-02-05

### Input Suggestions Problem
Claude Code's predictive text (greyed-out suggestions) was auto-completing answers before user could type them. Defeats the purpose of exercises.

**Solution:** Created project-specific `.claude/settings.json` with `{"inputSuggestions": false}`.

**Status:** Fixed and committed.

### Tool Call Visibility
User frustrated by seeing bash commands and tool output during exercises. Breaks immersion.

**Limitation:** Can't hide Claude Code's tool call display - it's built into the interface. Unlike file operations (which can be batched to wrap-up), audio playback must happen in real-time.

**Possible future solutions:**
1. Build a dedicated app UI that hides the scaffolding
2. Accept it as a limitation of the Claude Code prototype
3. Offer text-only mode for users who find it too distracting

---

## Future Feedback

[Add new feedback as collected]
