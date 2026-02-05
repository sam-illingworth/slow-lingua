# Slow Lingua

**Language Learning with Claude Code**

A calm, focused language learning system powered by Claude. No gamification, no streaks, no guilt — just steady progress.

Built using methodology from [Artificial Corner's language learning course](https://artificialcorner.com/s/language), adapted for Claude Code.

## What This Is

A structured system for learning languages using Claude as your tutor. Covers all four skills:
- **Speaking** — via speech-to-text (Wispr Flow, macOS Dictation, or similar)
- **Listening** — via text-to-speech (macOS `say` command)
- **Reading** — comprehension exercises with texts at your level
- **Writing** — composition with correction and feedback

## Philosophy

- **Task-based learning** — Learn through real situations (introducing yourself, ordering food, describing your day), not abstract grammar drills
- **Adaptive difficulty** — Moves at your pace based on actual performance
- **No gamification** — No points, streaks, badges, or guilt. Just learning.
- **Grammar in context** — Rules explained when you encounter them, not in isolation
- **"What did you mean?"** — When you make mistakes, Claude helps you say what YOU wanted to say

## Requirements

- [Claude Code](https://claude.ai/code) (requires Claude Pro subscription)
- macOS recommended (for `say` command text-to-speech)
- Speech-to-text tool recommended (Wispr Flow, macOS Dictation, or similar)

## Quick Start

1. Clone this repo:
   ```bash
   git clone https://github.com/sam-illingworth/slow-lingua.git
   cd slow-lingua
   ```

2. Open Claude Code in this directory:
   ```bash
   claude
   ```

3. Claude will read `CLAUDE.md` and either:
   - Run onboarding (if you're new)
   - Start a session (if you have an existing profile)

## Supported Languages

Currently configured:
- French
- Spanish

Easy to add more — copy a language file in `app/languages/` and adapt.

## How It Works

### Onboarding (first time)
- Choose your language
- Quick assessment to find your level
- Set goals and time commitment
- Get honest reality check on timeline

### Daily Sessions (~30 mins)
1. **Review** — Quick quiz on recent material
2. **New content** — Current task with mixed exercises
3. **Practice** — Conversation or extended exercise
4. **Wrap-up** — Summary, preview next session

### Example Session

Here's what a session looks like:

```
Claude: Welcome back. This is session 3. How are you feeling about French today?
        1. Fresh and ready
        2. A bit tired but willing
        3. Struggling - keep it light

You: 1

Claude: Great. Let's start with a quick review.

        [Audio plays: "Bonjour, je m'appelle Marie."]

        What did she say?

You: Hello, my name is Marie

Claude: Correct! Now your turn. How would you say "My name is Sam"?

You: Je m'appelle Sam

Claude: Perfect. Now a new phrase. Listen carefully.

        [Audio plays: "J'habite à Paris."]

        This means "I live in Paris."
        - "J'habite" = I live
        - "à" = in (for cities)

        How would you say "I live in Edinburgh"?

You: J'habite a Edinburgh

Claude: Almost! You need the accent: "J'habite à Edinburgh."
        The à (with accent) means "in" or "at" for locations.
        Without the accent, "a" means "has" - different word entirely.

        Try again?

You: J'habite à Edinburgh

Claude: Good. Let's practise a few more...
```

### Progress Tracking
Your progress saves to markdown files in `progress/[language]/`:
- Vocabulary with accuracy tracking
- Grammar points covered
- Common errors (for focused practice)
- Session logs

## Folder Structure

```
├── CLAUDE.md                 # Instructions for Claude (start here)
├── README.md                 # This file
├── app/
│   ├── onboarding.md         # New user flow
│   ├── curriculum.md         # 20 tasks, A1→B2
│   ├── user-profile.md       # Your settings and goals
│   ├── feedback.md           # App development notes
│   └── languages/            # Language-specific configs
│       ├── french.md
│       └── spanish.md
├── progress/                 # Your learning progress
│   └── [language]/
│       ├── current-status.md
│       ├── vocabulary.md
│       └── sessions/
├── content/                  # Reading materials (add your own)
└── design/
    └── branding.md           # Design principles
```

## Customisation

### Adding a language
Copy `app/languages/french.md`, rename, and adapt the phrases and grammar notes.

### Adjusting session length
Edit your `app/user-profile.md` — Claude will adapt accordingly.

### Adding reading materials
Add texts to `content/[language]/stories/` — Claude will use them for reading exercises.

## Bonus: Ralph Loop Pattern

This repo includes reusable files for the **Ralph Loop** context management pattern — a technique for maintaining AI effectiveness across long sessions by checkpointing state to external files.

- `ralph-loop-skill.md` — Full explanation with setup guide and examples
- `ralph-loop-minimal.md` — Drop-in template for any project

Copy these to your other Claude Code projects to prevent context degradation.

## Troubleshooting

### "say" command not found (Windows/Linux)

The listening exercises use macOS text-to-speech (`say` command). On other platforms:

- **Windows:** Install a TTS tool like [Balabolka](http://balabolka.site/balabolka.htm) or use browser-based TTS. Update the commands in `CLAUDE.md` to match.
- **Linux:** Install `espeak` or `festival` (`sudo apt install espeak`). Replace `say -v Thomas` with `espeak -v fr`.
- **Alternative:** Skip audio exercises and focus on reading/writing, or use an online TTS service.

### Setting up speech-to-text

Speaking exercises work best with speech-to-text so Claude can evaluate your pronunciation. Here are your options:

**Option 1: macOS Dictation (Free, built-in)**

1. Open System Settings → Keyboard → Dictation
2. Turn Dictation on
3. Choose your language (add French, Spanish, etc.)
4. Set shortcut to "Press Fn Key Twice" (default)
5. To use: press Fn twice, speak, press Fn twice again to stop

Pros: Free, no install, supports multiple languages
Cons: Requires internet, slight delay, can be finicky with accents

**Option 2: Wispr Flow (Recommended)**

1. Download from [wispr.com](https://www.wispr.com/)
2. Install and grant microphone permissions
3. Set up your activation method (default: hold Fn key)
4. Works anywhere you can type, including Claude Code

Pros: Fast, accurate, works offline, handles accents well
Cons: Paid subscription after trial

**Option 3: No speech-to-text**

You can still do speaking exercises:
- Speak your answer aloud for pronunciation practice
- Type what you said for Claude to evaluate
- Less immediate feedback, but still valuable practice

To skip speaking exercises entirely, tell Claude at the start of your session: "Focus on reading and writing today, skip speaking exercises."

### Claude Code not starting

Make sure you have:
1. A Claude Pro subscription
2. Claude Code installed: `npm install -g @anthropic-ai/claude-code`
3. Run `claude` from within the slow-lingua directory

### Session not resuming correctly

If Claude starts fresh instead of resuming:
- Check that `progress/[language]/session-state.md` exists
- Make sure the previous session ended properly (status should be "idle" or "in_progress")
- If files are corrupted, delete `session-state.md` and start fresh

## Credits

- Methodology adapted from [Artificial Corner](https://artificialcorner.com/s/language)
- Ralph Loop pattern from [snarktank/ralph](https://github.com/snarktank/ralph)
- Built with [Claude Code](https://claude.ai/code)

## License

MIT — use it, adapt it, share it.

---

*Part of the [Slow AI](https://theslowai.substack.com/) project.*
