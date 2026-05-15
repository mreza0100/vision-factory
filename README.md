# Vision Factory

**Version:** 1.0.0 · **License:** MIT · **Repo:** [github.com/mreza0100/vision-factory](https://github.com/mreza0100/vision-factory)

A Claude Code skill that forges, validates, and stress-tests startup visions through three sequential modes: a Socratic interview that grills the founder until the real vision emerges, a cross-check that produces a targeted research prompt, and a ten-dimension rubric that scores the vision honestly.

## Why this exists

Most founders articulate their vision badly — not because they lack one, but because they've never been forced to defend it against hard questions. Pitch decks are polished. Elevator pitches are rehearsed. But when someone asks "why should this exist?" and won't accept a vague answer, the real vision either emerges or reveals that it doesn't exist yet.

The skill is a structured protocol for that conversation.

## How it works

### Three modes

| Mode                | Input                                                 | Output                                           |
| ------------------- | ----------------------------------------------------- | ------------------------------------------------ |
| **A — CREATE**      | Founder context                                       | Vision narrative + one-pager                     |
| **B — RESEARCH**    | Vision draft + domain knowledge                       | Claims assessment + scoped research prompt (RRP) |
| **C — STRESS-TEST** | Vision draft + research (optional) + domain knowledge | Scored rubric (10 dimensions) + hardened vision  |

Modes chain: A → B → C → optional loop back to A with findings. Each mode can also be invoked independently.

### Mode A: CREATE — The Grilling

A Socratic interview that asks eight questions, one at a time, pushing back on vague answers until the responses are specific enough to build a narrative from. Questions draw from YC's evaluation criteria, Peter Thiel's contrarian truth framework, Sequoia's "why now?" template, and Hamilton Helmer's 7 Powers moat framework.

From the interview answers, the skill constructs: a vision statement (1 sentence), an origin story, a problem→solution narrative, a contrarian position, and a one-pager.

### Mode B: RESEARCH — The Cross-Check

Extracts testable claims from the vision draft, cross-checks them against available domain knowledge, and produces a well-targeted Research Report Prompt (RRP) for the claims that are unsupported or contradicted. The RRP is designed to be run via your project's research skill.

### Mode C: STRESS-TEST — The Rubric

Scores the vision across ten dimensions (market, problem, solution fit, timing, moat, founder-market fit, business model, regulatory, competition, execution risk). Each dimension gets PASS / CONDITIONAL / FAIL with evidence and specific next actions. The final verdict is GREEN / YELLOW / RED.

Supports domain-specific overlays — health-tech, fintech, marketplace, enterprise SaaS — that add sub-questions without changing the ten core dimensions.

## Directory structure

```
vision-factory/
├── SKILL.md                           # Core protocol (three modes, rubric, rules)
├── README.md                          # This file
├── LICENSE                            # MIT
├── .gitignore
├── references/
│   ├── interview-frameworks.md        # Deep methodology for each Socratic question
│   └── rubric-methodology.md          # Scoring rules, anti-inflation, domain overlays
├── profiles/                          # Domain voice profiles (gitignored except built-in)
└── tmp/                               # Working artifacts (gitignored)
```

## Integrating with your project

This skill is general-purpose. To integrate:

1. Copy or symlink the `vision-factory/` directory into your project's skill directory
2. In your consuming command (e.g., a mentor or advisor command), add hooks that:
   - Point to your domain-specific reference docs (competitive intelligence, regulatory knowledge, etc.)
   - Specify where to save artifacts
   - Add domain-specific rubric overlay if needed
   - Specify a voice profile for narrative output (if using a ghostwriter-style skill)

The skill protocol stays clean. Your command adds the domain context.

## Frameworks referenced

| Framework          | Source                | Used in              |
| ------------------ | --------------------- | -------------------- |
| Jobs-to-be-Done    | Christensen (2003)    | Mode A Q1            |
| The Mom Test       | Fitzpatrick (2013)    | Mode A Q2            |
| 10x Better Test    | Thiel (2014), YC      | Mode A Q3            |
| Founder-Market Fit | Andreessen (2007), YC | Mode A Q4            |
| "Why Now?"         | Sequoia, Gross (2015) | Mode A Q5            |
| 7 Powers           | Helmer (2016)         | Mode A Q6, Mode C D5 |
| Contrarian Truth   | Thiel (2014)          | Mode A Q7            |
| Definite Optimism  | Thiel (2014)          | Mode A Q8            |
| Insurgent Mission  | Zook & Allen (2016)   | Mode A Q8            |
| Pre-mortem         | Klein (2004, 2007)    | Mode C D10           |
| Lean Canvas        | Maurya (2012)         | Mode B               |

## License

MIT — see LICENSE file.
