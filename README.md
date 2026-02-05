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

## Why Not Duolingo?

Duolingo is great for what it does. But it's designed to maximise engagement, not learning. Streaks, hearts, leaderboards, and notifications keep you coming back — but also create guilt when you miss a day.

Slow Lingua is different:

| | Duolingo | Slow Lingua |
|---|----------|-------------|
| **Goal** | Keep you engaged | Help you learn |
| **Motivation** | Streaks, XP, leagues | Intrinsic (your own goals) |
| **Missed a day?** | Streak lost, guilt | Nothing happens |
| **Mistakes** | Marked wrong | "What did you mean?" |
| **Grammar** | Minimal explanation | Explained in context |
| **Pace** | App decides | You decide |
| **Cost** | Free (with ads) or $7/mo | $20/mo (Claude Pro) |

**Slow Lingua is for you if:**
- You're tired of gamification and guilt
- You want grammar explained, not just pattern-matched
- You prefer 30 focused minutes over 5 distracted ones
- You're comfortable with a CLI tool
- You already have Claude Pro

**Stick with Duolingo if:**
- You need external motivation (streaks work for you)
- You want a polished mobile app
- You're on a tight budget
- You prefer short 5-minute sessions

No judgement either way. Use what works for you.

## What This Tool Is (and Isn't)

**Slow Lingua is best for: A0 → B1** (complete beginner to intermediate)

The structured curriculum covers introducing yourself through to expressing opinions and telling stories. This is where AI tutoring shines — patient repetition, instant feedback, adaptive pacing.

**B2 and beyond benefits from human connection.**

At upper-intermediate and advanced levels, you need:
- Real conversations with unpredictable responses
- Cultural nuance that comes from lived experience
- The social motivation of learning with others
- Feedback on subtleties that AI can miss

This isn't a limitation — it's the point. AI should help you build foundations, not replace human connection. Once you reach B1, find a conversation partner, tutor, or language exchange. Use Slow Lingua for grammar review and vocabulary expansion, but prioritise human practice.

This is the Slow AI philosophy: know when to use AI and when to leave it alone.

## Known Limitations

This is a prototype built in Claude Code, not a polished app. Some rough edges:

**Tool call visibility:** You'll see technical output (bash commands, file operations) during exercises. This can break immersion, especially during listening exercises where the phrase appears before the audio plays. There's no way to hide this in Claude Code's interface.

**Input suggestions:** Claude Code may show greyed-out predictive text that auto-completes your answers. This defeats the purpose of exercises. The repo includes a `.claude/settings.json` that disables this, but you may need to restart Claude Code for it to take effect.

**Audio limitations:** Listening exercises use macOS text-to-speech. The quality is decent but robotic. Real language learning benefits from hearing native speakers with natural rhythm and intonation.

**No mobile app:** This runs in a terminal. You can't use it on your phone during your commute.

**Session interruptions:** If Claude Code crashes or you close the terminal mid-session, progress since the last checkpoint may be lost. The system saves at wrap-up, not continuously.

These are acceptable trade-offs for a free, adaptable prototype. If you want polish, use Duolingo. If you want flexibility and depth, this works.

## Requirements

**Cost:** This app requires a [Claude Pro subscription](https://claude.ai/pro) ($20/month). There is no free tier.

- [Node.js](https://nodejs.org/) 18 or higher
- [Claude Code](https://claude.ai/code) CLI tool
- macOS recommended (for `say` command text-to-speech)
- Speech-to-text tool recommended (Wispr Flow, macOS Dictation, or similar)

**Platform notes:**
- **macOS:** Full support (audio + speech)
- **Windows/Linux:** Works, but requires alternative TTS setup (see Troubleshooting)

## Quick Start

1. **Install Claude Code** (if you haven't already):
   ```bash
   npm install -g @anthropic-ai/claude-code
   ```
   If you see "npm: command not found", install [Node.js](https://nodejs.org/) first.
   If you see "permission denied", try: `sudo npm install -g @anthropic-ai/claude-code`

2. **Clone this repo:**
   ```bash
   git clone https://github.com/sam-illingworth/slow-lingua.git
   cd slow-lingua
   ```

3. **Start Claude Code:**
   ```bash
   claude
   ```
   You'll need to log in with your Claude Pro account on first run.

4. Claude will read `CLAUDE.md` and either:
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

1. Download from [wisprflow.ai](https://wisprflow.ai/r?SAM2113)
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
