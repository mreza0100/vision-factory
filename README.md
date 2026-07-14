# Vision Factory

**Version:** 2.2.1 · **License:** MIT

A skill that forges, validates, and stress-tests a startup vision using Paul Graham's actual filters — not generic VC frameworks.

## Why this exists

Most founders articulate their vision badly. Not because they lack one, but because they've never been forced to defend it against hard questions from someone who's seen ten thousand pitches. Pitch decks are polished. Elevator pitches are rehearsed. But when someone asks *"who, by name, wants this so badly they'd use a crappy v1?"* and won't accept a vague answer — the real vision either emerges or reveals that it doesn't exist yet.

This skill is a structured protocol for that conversation, grounded in PG's essays.

## What changed in v2

v1 was a generic protocol that referenced PG once at the bottom of an "additional reading" table. The 8 Socratic questions were synthesized from Christensen, Thiel, Sequoia, Helmer, Andreessen — competent but generic.

v2 is grounded in PG end-to-end:

- The 8 questions are PG-shaped (organic origin, Buchheit test, crappy v1, schlep, living-in-the-future, contrarian-with-mechanism)
- The 10-filter rubric replaces the generic 10-dimension VC rubric (organic, well, Buchheit, schlep, crowded-market thesis, leading-edge, right-kind-of-stubborn, ambition, survival, top-idea-in-mind)
- Reference docs are distilled from PG's essays into `references/pg-*.md`
- The multi-profile / consumer-integration scaffolding from v1 is gone — this is one opinionated thing, not a pluggable framework

## What changed in v2.1

Mode A's grilling got sharper, borrowing three mechanics from the YC office-hours diagnostic:

- **Anti-sycophancy guardrails** — an explicit list of soft hedge-phrases to avoid, plus worked soft-vs-forcing examples so the interview pushes instead of validates.
- **Stage-aware routing + an escape hatch** — the eight questions now route by founder stage (pre-product → has paying customers) instead of always asking all eight, and there's a graceful path when the founder says "just do it."
- **"What I noticed about how you think"** — a sixth Mode A artifact that reflects founder signals (named real users, defended premises, lived edge, taste, agency) back to the founder, the way a good mentor closes a hard conversation.

## What changed in v2.2

The chain no longer abandons the founder at the cliff edge of "go talk to customers." A fourth mode closes the loop, plus two evidence-discipline upgrades:

- **Mode D — FIELD-VALIDATE** — turns each unproven scorecard filter into the customer-interview kit that would flip it (research plan + behavior-based screener + Mom-Test interview guide), then synthesizes returned transcripts into a re-score. The bridge between STRESS-TEST and "go build."
- **Outcome-verb + decision-mapping in Mode B** — every testable claim becomes a finite, falsifiable question that names the decision it informs; sideshow claims get cut.
- **≥2-source groundedness in Mode C** — a CONDITIONAL flips to PASS only on two independent real sources, never one vivid quote. One source is a story; two is a pattern.

The interview craft is borrowed from established discovery methodology but kept PG-native — no persona taxonomies, JTBD frameworks, or prioritization matrices.

## How it works

Four modes that chain (A → B → C → D → optional loop), each of which can also be invoked standalone.

| Mode | Input | Output |
|------|-------|--------|
| **A — CREATE** | Founder context | Vision narrative + one-pager (PG-style) |
| **B — RESEARCH** | Vision draft + available knowledge | Validation report with executed research |
| **C — STRESS-TEST** | Vision draft + research (optional) | 10-filter PG rubric + hardened vision |
| **D — FIELD-VALIDATE** | Scorecard CONDITIONALs + returned transcripts | Interview kit + synthesized re-score |

### Mode A: CREATE — The Grilling

Eight questions, asked one at a time, pushing back on vague answers. Not "what's your TAM?" — "walk me through the moment you first ran into this problem yourself." Not "what's your moat?" — "what's the schlep you're willing to do that scares everyone else off?"

Push-back rules enforce specificity: no nameless users, no jargon, no resume-as-credentials, no press-release 5-year pictures, no frictionless-growth fantasies.

Output: vision statement (≤20 words), origin story, problem→solution narrative, contrarian thesis, a one-page summary, and a short "what I noticed about how you think" reflection.

### Mode B: RESEARCH — The Cross-Check

Extracts testable claims from the draft, cross-checks against available knowledge, executes research internally for unsupported claims, returns a validation report. The user never sees intermediate research prompts. PG-grounded research targets Mom Test evidence (current behavior > stated preferences), real names in forums and support tickets, leading-edge fact-checks — not generic market-sizing.

### Mode C: STRESS-TEST — PG's 10 Filters

Scores the vision across 10 filters: ORGANIC, WELL, BUCHHEIT, SCHLEP, CROWDED-MARKET THESIS, LIVING-IN-THE-FUTURE, RIGHT-KIND-OF-STUBBORN, AMBITION, SURVIVAL, TOP-IDEA-IN-MIND. Each gets PASS / CONDITIONAL / FAIL with evidence quoted from the vision and a specific action for any gap.

Filters 1-3 are load-bearing — a FAIL on any of them means the vision doesn't yet exist as a real thing. The other seven are fixable.

Verdict: GREEN (8+ PASS, 0 FAIL on load-bearing) → go build · YELLOW (5-7 PASS) → sharpen and revise · RED (<5 PASS or load-bearing FAIL) → rethink.

### Mode D: FIELD-VALIDATE — Close the Loop

Turns the scorecard's unproven filters into a real customer-interview kit, then folds the results back into a re-score. For each CONDITIONAL/FAIL filter it writes the past-behavior questions that would move it, produces a research plan + behavior-based screener + Mom-Test interview guide, and — after the founder runs the interviews — synthesizes the transcripts and re-scores (a CONDITIONAL flips to PASS only on ≥2 independent real sources). The founder runs the interviews; synthetic participants are never a substitute for real ones.

## Directory structure

```
vision-factory/
├── SKILL.md                              # The protocol (three modes, rules)
├── README.md                             # This file
├── LICENSE                               # MIT
├── INSTALLED.md                          # Install notes
├── .gitignore
└── references/
    ├── pg-on-ideas.md                    # How to tell a real idea from a sitcom one
    ├── pg-on-founders.md                 # What to look for in the founder behind the vision
    ├── pg-on-ambition.md                 # How to evaluate the scale of the vision
    ├── pg-on-survival.md                 # Can this vision survive contact with reality
    ├── pg-voice.md                       # How to write the output
    ├── pg-filters.md                     # Consolidated 10-filter rubric for Mode C
    └── field-validate.md                 # Mode D: CONDITIONAL→questions, interview craft, re-score
```

## Frameworks referenced

PG's essays are the only source. The skill references these directly:

- *How to Get Startup Ideas* (2012) — the three qualities, the well, organic vs sitcom, schlep blindness
- *Schlep Blindness* (2012) — what nobody else wants to build is often the best idea
- *Organic Startup Ideas* (2010) — Apple-type vs Viaweb-type, "what do you wish someone would build for you"
- *What We Look for in Founders* (2010) — determination, flexibility, imagination, naughtiness, friendship
- *The Anatomy of Determination* (2009) — willfulness × discipline, aimed by ambition
- *The Right Kind of Stubborn* (2024) — persistent vs obstinate
- *Frighteningly Ambitious Startup Ideas* (2012) — the blurry vision, head west
- *Default Alive or Default Dead?* (2015) — the survival question
- *Do Things that Don't Scale* (2013) — manual user recruitment, insane delight
- *Founder Mode* (2024) — what the 5-year picture should look like
- *Startups in 13 Sentences* (2009) — understand your users
- *The Top Idea in Your Mind* (2010) — shower-thinking as the deep diagnostic
- *Startup = Growth* (2012) — growth as the compass
- *The 18 Mistakes That Kill Startups* (2006) — the failure modes
- *How to Think for Yourself* (2020) — the contrarian-with-mechanism shape
- *How to Start Google* (2024) — leading-edge perception of "missing things"

## License

MIT — see LICENSE file.
