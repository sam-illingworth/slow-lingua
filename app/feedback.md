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

---

## Future Feedback

[Add new feedback as collected]
