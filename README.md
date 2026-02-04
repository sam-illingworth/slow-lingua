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

## Credits

- Methodology adapted from [Artificial Corner](https://artificialcorner.com/s/language)
- Built with [Claude Code](https://claude.ai/code)

## License

MIT — use it, adapt it, share it.

---

*Part of the [Slow AI](https://theslowai.substack.com/) project.*
