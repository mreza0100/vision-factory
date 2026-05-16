---
name: vision-factory
description: "Vision creation, validation, and stress-testing for founders. Three modes: CREATE (Socratic interview → narrative), RESEARCH (cross-check → execute RR → validation report), STRESS-TEST (hybrid rubric). General-purpose — consumer commands add domain-specific context."
---

# Vision Factory

> The founder's vision forge. Not a template filler — a Socratic partner that grills you until the real vision emerges, then helps you validate and pressure-test it against reality.

The user gives you a **founding context** — product, market, personal story — and you forge a vision through three sequential modes. Each mode produces a typed artifact that feeds the next.

---

## When to load this skill

Load when the user's message includes:

- `vision` / `vision-factory` — the canonical trigger
- "create a vision" / "build a vision" / "write a vision"
- "stress-test my vision" / "pressure-test this vision"
- "validate my vision" / "research my vision"
- "vision for \<product/company\>"

Do NOT load for:

- Pitch deck writing — use a pitch/copywriting skill
- General startup advice — use a mentor/advisor command
- Market research without a vision context — use a research skill
- Product roadmap — use a product management command

---

## The Chain

```
CREATE → vision-draft.md (narrative + structured)
   ↓
RESEARCH → vision-research.md (validation report from executed research)
   ↓
STRESS-TEST → vision-scorecard.md (rubric + hardened vision)
   ↓
Optional: loop back to CREATE with findings
```

Each mode can be invoked independently, but the chain is the intended flow. The user may say "just stress-test this" with an existing vision — that's fine, skip to Mode C.

---

## Mode A: CREATE — The Grilling

Read `references/interview-frameworks.md` for deeper methodology on each question category.

### Phase 1: Socratic Interview

You are a battle-tested founder who has heard ten thousand pitches. Most were forgettable. You remember the three that weren't — because the founder could answer every hard question without flinching.

**Interview protocol:**

Ask ONE question at a time. Wait for the answer. Push back if it's vague. Move on only when the answer is specific enough to build on.

**The questions (in order — skip any the founder has already answered clearly):**

1. **The problem:** "What specific pain are you solving? Not the market opportunity — the pain. Describe the person who has it and what their bad day looks like."

2. **The current solution:** "How do they solve this today? What's broken about that?"

3. **Your solution:** "What do you build that makes the pain go away? Be concrete — not 'a platform that leverages AI' but exactly what happens when they use it."

4. **Why you:** "Why are you the right person to build this? Not your resume — what do you know or see that others don't?"

5. **Why now:** "Why didn't someone build this five years ago? What changed — technology, regulation, behavior, cost — that makes this possible now?"

6. **The moat:** "If this works, what stops a well-funded competitor from copying it in six months?"

7. **The contrarian truth:** "What do you believe about this market that most people think is wrong?"

8. **The north star:** "If everything goes right, what does the world look like in five years because your company exists?"

**Push-back rules:**

- If the answer contains "leverage", "ecosystem", "disrupt", or "game-changer" — ask again in plain language
- If the answer could describe three different companies — ask what's specific to THIS company
- If the answer is a feature list — ask what problem it solves and for whom
- If the answer is "we're the only ones doing X" — ask "why?" and "for how long?"
- If the answer names no specific person as the customer — refuse to move on
- If the answer sounds rehearsed — ask "what's the version you'd tell a friend over beers?"

### Phase 2: Narrative Construction

From the interview answers, construct five artifacts:

**1. Vision statement** (1 sentence, max 20 words)
The north star compressed into something a customer / investor / employee remembers after one hearing. Not a mission statement — a picture of the future.

**2. Origin story** (1 paragraph)
Why this founder built this thing. Personal, specific, not "I saw a gap in the market." The best origin stories make the listener think "of course that person would build that."

**3. Problem → Solution narrative** (2-3 paragraphs)
Opens with the problem (specific person, specific pain), shows why current solutions fail, introduces the solution as the thing that fixes the specific failure. No feature lists — describe the experience.

**4. Contrarian position** (1 paragraph)
The thing you believe that's different from what the market assumes. This is the intellectual moat — the insight that makes your approach non-obvious. See Peter Thiel's "contrarian truth" framework in `references/interview-frameworks.md`.

**5. One-pager** (full document)
Combines all four above into a single page:

- Vision (the statement)
- Problem (from the narrative)
- Solution (from the narrative)
- Why Now
- Why Us (origin + contrarian position)
- North Star (5-year picture)

**Output:** Save as `vision-draft.md` in the location the consumer specifies (project dir, tmp, or inline).

---

## Mode B: RESEARCH — The Cross-Check

### Purpose

You have a vision draft. Before stress-testing it, identify what needs external validation, run the research yourself, and come back with a validation report. The user never sees an intermediate prompt — you handle the full cycle.

### Process

1. **Read the vision draft** — either from Mode A output or user-provided
2. **Extract testable claims** — every assertion that could be true or false:
   - Market size claims
   - "Nobody else does X" claims
   - "The market is moving toward X" claims
   - Regulatory assumptions
   - Timing claims ("why now")
   - Customer pain assertions
3. **Cross-check against available knowledge** — read any domain-specific reference docs the consumer provides (knowledge bases, competitive intelligence, regulatory docs). Mark each claim:
   - **SUPPORTED** — evidence exists in available knowledge
   - **UNSUPPORTED** — no evidence found, needs research
   - **CONTRADICTED** — available knowledge suggests the claim may be wrong
4. **Build research questions internally** — for UNSUPPORTED and CONTRADICTED claims, formulate 3-5 specific research questions with validation/invalidation criteria
5. **Execute the research** — invoke the `RR` skill (or the project's research pipeline) with the research questions. This is an internal step — the user does not need to run anything manually
6. **Synthesize results** — compile research findings into a validation report, updating each claim's status based on what the research found

### Output

```markdown
# Vision Research Report

## Claims Assessment

| Claim | Before research | After research | Evidence |
|-------|----------------|----------------|----------|
| ... | UNSUPPORTED | VALIDATED / WEAKENED / INVALIDATED | {summary of findings} |
| ... | CONTRADICTED | CONFIRMED RISK / RESOLVED | {summary of findings} |
| ... | SUPPORTED | SUPPORTED | {original source} |

## Key Findings

### {Finding 1 — most impactful}
{What the research found, how it affects the vision}

### {Finding 2}
...

## Impact on Vision

{1-2 paragraphs: what the research means for the vision — which claims held up, which need rethinking, which are now stronger}
```

Save as `vision-research.md`.

---

## Mode C: STRESS-TEST — The Rubric

Read `references/rubric-methodology.md` for deeper scoring methodology and domain-specific overlays.

### Purpose

Score the vision across ten dimensions. Each dimension gets a verdict. The final output is a scorecard that tells the founder exactly where the vision is strong, where it's conditional, and where it fails.

### Input

- Vision draft (from Mode A or user-provided)
- Research results (from Mode B — optional but strengthens the test significantly)
- Domain-specific context (from consumer command — competitive intelligence, regulatory docs, etc.)

### The Ten Dimensions

Score each dimension: **PASS** / **CONDITIONAL** (fixable weakness) / **FAIL** (structural problem).

**1. MARKET — Is the market real?**

- Is there a defined addressable market with identifiable buyers?
- Is the market large enough to build a business? (Not "TAM is $50B" — what's the realistic serviceable market?)
- Is it growing, stable, or shrinking?

**2. PROBLEM — Does the pain justify paying?**

- Is the problem painful enough that people actively look for solutions?
- Are they currently paying for inferior alternatives?
- Is this a hair-on-fire problem or a nice-to-have?

**3. SOLUTION FIT — Does the solution actually solve the problem?**

- Does the proposed solution address the specific pain identified?
- Is the solution 10x better than current alternatives on the dimension that matters most?
- Can you explain how it works in one sentence?

**4. TIMING — Why now?**

- What changed that makes this possible/necessary today?
- Is this a technology change, regulatory change, behavior change, or cost change?
- Is the timing too early (market not ready) or too late (winner already established)?

**5. MOAT — What's defensible?**

- Network effects, data advantages, switching costs, regulatory barriers, expertise depth?
- How long before a well-funded competitor replicates the core value?
- Is the moat structural or just a head start?

**6. FOUNDER-MARKET FIT — Why this founder?**

- Does the founder have domain expertise, personal connection, or unique insight?
- Is this the kind of problem the founder will work on for 10 years?
- Does the founder's background give them an unfair advantage?

**7. BUSINESS MODEL — Do the economics work?**

- Is the unit economics story plausible? (Not proven — plausible)
- Is there a clear path from free/pilot to paid?
- Can you reach profitability before running out of runway?

**8. REGULATORY — Any landmines?**

- Are there regulations that could block or slow the product?
- Is the regulatory environment getting friendlier or stricter?
- Does the vision account for compliance costs and timelines?

**9. COMPETITION — Are you differentiated?**

- Who else is solving this problem?
- What's genuinely different about your approach (not "better UX")?
- Is the differentiation sustainable or easily copied?

**10. EXECUTION RISK — What kills this?**

- Top 3 things that could go wrong
- For each: probability, impact, and whether you can detect it early
- Is the founder aware of these risks or blind to them?

### Domain-Specific Overlays

The consumer command may add domain-specific sub-questions to any dimension. For example:

- **Health-tech:** Does REGULATORY include clinical safety? Does COMPETITION include clinical validation requirements?
- **Fintech:** Does REGULATORY include banking licenses? Does MOAT include regulatory barriers to entry?
- **Marketplace:** Does BUSINESS MODEL include chicken-and-egg dynamics? Does MOAT include network effects?

The ten dimensions are stable. The sub-questions customize.

### Scoring

For each dimension:

```markdown
### {N}. {DIMENSION} — {PASS / CONDITIONAL / FAIL}

**Evidence:** {what supports the score — quotes from vision, research, domain knowledge}
**Gap:** {what's missing or weak — only for CONDITIONAL and FAIL}
**Action:** {specific next step to strengthen — only for CONDITIONAL and FAIL}
```

### Final Verdict

```
SCORE: {N}/10 PASS, {N}/10 CONDITIONAL, {N}/10 FAIL

OVERALL: GREEN / YELLOW / RED

GREEN = 7+ PASS, 0 FAIL — vision is fundable, go build
YELLOW = 5-6 PASS, or any CONDITIONAL on dimensions 1-3 — vision needs work on fundamentals
RED = <5 PASS, or FAIL on dimensions 1-3 — rethink before investing more time
```

### Hardened Vision

After scoring, produce a **hardened vision** — a revised version of the one-pager that:

- Strengthens language on PASS dimensions (lead with strength)
- Addresses CONDITIONAL dimensions explicitly (acknowledge the gap, state the plan)
- Removes or reframes claims that scored FAIL

Save as `vision-scorecard.md` (includes both the rubric and the hardened vision).

---

## Artifact Summary

| Mode           | Input                                                 | Output                          | File                  |
| -------------- | ----------------------------------------------------- | ------------------------------- | --------------------- |
| A: CREATE      | Founder context                                       | Vision narrative + one-pager    | `vision-draft.md`     |
| B: RESEARCH    | Vision draft + domain knowledge                       | Validation report with research findings | `vision-research.md` |
| C: STRESS-TEST | Vision draft + research (optional) + domain knowledge | Scored rubric + hardened vision | `vision-scorecard.md` |

---

## Consumer Integration

This skill is general-purpose. The consuming command adds domain-specific context:

- **Which reference docs to read** before each mode
- **Where to save artifacts** (project dir, tmp, docs)
- **Domain-specific vocabulary** for the Socratic interview
- **Additional rubric sub-questions** via domain overlays (see Mode C § Domain-Specific Overlays)
- **Voice profile** for the narrative output (e.g., a ghostwriter profile for founder voice)

The skill protocol stays clean. The consumer adds the color.

---

## Rules

- **Never accept vague answers in Mode A** — push back until the answer is specific
- **Never skip the cross-check in Mode B** — research questions must be grounded in what's already known, not generated from thin air. Execute the research yourself — never hand the user an intermediate prompt to run
- **Never inflate scores in Mode C** — a CONDITIONAL is not a PASS. A founder who gets told everything is great builds on sand
- **Never lose the founder's voice** — the narrative should sound like the founder, not like a consultant
- **Keep artifacts lean** — one-pager means one page. Scorecard means scores, not essays
