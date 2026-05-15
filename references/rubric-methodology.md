# Rubric Methodology — How to Score Honestly

> Where the ten dimensions come from, how to score each one without inflating, and how to add domain-specific overlays.

This reference deepens Mode C. The SKILL.md has the rubric structure. This document has the methodology, the anti-inflation rules, and the framework for domain customization.

---

## Why Ten Dimensions

The ten dimensions synthesize evaluation frameworks from four sources:

1. **Y Combinator's application criteria** — problem, solution, market, founder-market fit, traction
2. **Sequoia Capital's pitch template** — company purpose, problem, solution, why now, market size, competition, product, business model, team
3. **Hamilton Helmer's 7 Powers** — moat classification
4. **Gary Klein's pre-mortem technique** — execution risk identification

The mapping:

| Dimension             | Primary source         | Why it's here                   |
| --------------------- | ---------------------- | ------------------------------- |
| 1. MARKET             | Sequoia, YC            | No market = no business         |
| 2. PROBLEM            | YC, Christensen (JTBD) | Pain drives payment             |
| 3. SOLUTION FIT       | YC, Thiel (10x test)   | Solution must match pain        |
| 4. TIMING             | Sequoia, Gross         | #1 predictor of startup success |
| 5. MOAT               | Helmer (7 Powers)      | Durability of advantage         |
| 6. FOUNDER-MARKET FIT | YC, Andreessen         | Right founder for right problem |
| 7. BUSINESS MODEL     | Sequoia                | Economics must be plausible     |
| 8. REGULATORY         | Domain-specific        | Landmines you can't ignore      |
| 9. COMPETITION        | Sequoia, Porter        | Differentiation must be real    |
| 10. EXECUTION RISK    | Klein (pre-mortem)     | What kills this in practice     |

Dimensions 1-3 are **foundational** — a FAIL on any of them means the vision has a structural problem. Dimensions 4-10 are **conditional** — weaknesses are fixable if the foundation is sound.

---

## Scoring Rules — Anti-Inflation Protocol

The biggest risk in rubric scoring is grade inflation. Founders want to hear good news. LLMs default to encouraging tone. The rubric must resist both.

### PASS requires

- Positive evidence — not just absence of problems
- The evidence must come from the vision document, research results, or domain knowledge — not from the founder's enthusiasm
- If the only evidence is "the founder believes this" — it's CONDITIONAL at best

### CONDITIONAL requires

- A specific, nameable gap — not "could be stronger"
- A specific action that would close the gap — not "needs more research"
- A realistic assessment of whether the gap is closable — some gaps are structural

### FAIL requires

- Evidence that contradicts the vision's claims, OR
- A structural problem that can't be fixed by iteration (e.g., the market doesn't exist, the problem isn't painful, the founder has no domain connection)
- FAIL is not a judgment of the founder — it's a signal to rethink this specific dimension

### Rules

- **Never round up.** If you're unsure between CONDITIONAL and PASS, score CONDITIONAL. The founder benefits more from a honest CONDITIONAL than a generous PASS.
- **Never score on potential.** Score on what's demonstrated or evidenced, not what could be true.
- **Never let narrative quality affect scores.** A beautifully written vision with a non-existent market still FAILS dimension 1.
- **Always state the evidence.** Every score must cite what it's based on — a quote from the vision, a research finding, a domain fact, or the absence of evidence.
- **FAIL is not fatal.** It means "rethink this dimension before proceeding." Many great companies scored FAIL on early visions and iterated.

---

## Dimension Deep-Dives

### 1. MARKET — The Reality Test

**PASS signals:**

- Named, identifiable buyers (not "small businesses" but "independent GGZ therapists in the Netherlands")
- Evidence of market size from research or industry data
- Growth trajectory — growing markets forgive mistakes

**CONDITIONAL signals:**

- Market exists but size is unclear
- Market is emerging (real but unproven at scale)
- Market is niche — viable for lifestyle business, questionable for VC-scale

**FAIL signals:**

- No identifiable buyer segment
- Market is shrinking
- "Everyone is our customer" (means no one is)

### 2. PROBLEM — The Pain Test

**PASS signals:**

- People actively seek solutions today (googling, buying alternatives, complaining in forums)
- Money already flows to inferior solutions (proves willingness to pay)
- The problem has emotional weight (anger, frustration, fear — not mild inconvenience)

**CONDITIONAL signals:**

- Problem exists but people aren't actively solving it (latent pain)
- Problem is real but willingness to pay is unproven
- The pain is organizational (company feels it) but individual users don't (adoption challenge)

**FAIL signals:**

- "Wouldn't it be nice if..." problems — no urgency
- The problem is the founder's, not the customer's
- Customers have a solution they're satisfied with (even if suboptimal)

### 3. SOLUTION FIT — The 10x Test

**PASS signals:**

- The solution directly addresses the #1 pain identified in dimension 2
- 10x improvement on at least one critical dimension (speed, cost, accuracy, convenience)
- Explainable in one sentence

**CONDITIONAL signals:**

- Solution is 2-5x better (significant but not switching-cost-overcoming)
- Solution addresses the problem but requires behavior change from users
- Multiple value props but no single killer feature

**FAIL signals:**

- Solution is a feature, not a product (nice addition but not worth switching for)
- Solution solves a problem the founder defined, not the customer defined
- "We're like X but better" without a specific dimension of 10x improvement

### 4. TIMING — The Window Test

**PASS signals:**

- A specific, identifiable change happened recently (technology, regulation, behavior, cost)
- The window is open now and will close (first-mover has meaningful advantage)
- Evidence that early adopters are already emerging

**CONDITIONAL signals:**

- The change is happening but slowly (may be too early)
- The timing thesis relies on prediction, not observation
- Multiple timing signals that partially conflict

**FAIL signals:**

- No identifiable timing catalyst ("we just think it's time")
- The window opened years ago and incumbents already moved
- The timing depends on a change that hasn't happened yet (regulatory, technology)

### 5. MOAT — The Durability Test

Apply Hamilton Helmer's 7 Powers framework. Score based on which powers the company is building:

**PASS signals:**

- At least one clear structural power (network effects, switching costs, counter-positioning)
- The moat deepens with time and usage
- Well-funded competitors would need years to replicate the advantage

**CONDITIONAL signals:**

- Data advantage exists but it's unclear if it's defensible
- Head start only — no structural barrier
- Moat is regulatory (real but could change)

**FAIL signals:**

- "First mover" is the only advantage
- No structural power identified
- The core value can be replicated by a large company in months

### 6-10 — Follow the same evidence → gap → action pattern. The sub-questions in SKILL.md Mode C provide the evaluation criteria for each.

---

## Domain-Specific Overlays

The ten dimensions are universal. The sub-questions customize per domain. Here's how to build an overlay:

### Structure

```markdown
## {Domain} Overlay

### Dimension modifications

| Dimension  | Additional sub-question               | Why               |
| ---------- | ------------------------------------- | ----------------- |
| REGULATORY | {domain-specific regulatory question} | {domain risk}     |
| MOAT       | {domain-specific moat question}       | {domain dynamics} |
| ...        | ...                                   | ...               |

### Additional dimension (if needed)

| Name            | Sub-questions | Threshold             |
| --------------- | ------------- | --------------------- |
| CLINICAL SAFETY | {questions}   | FAIL if not addressed |
```

### Example overlays

**Health-tech:**

- REGULATORY: "Does the product touch patient data? If yes, is HIPAA/GDPR compliance addressed? Is clinical safety considered?"
- MOAT: "Does usage generate clinical data that improves the product? Are there regulatory barriers to entry (certifications, approvals)?"
- PROBLEM: "Is the pain clinical (affects patient outcomes), administrative (affects workflows), or both?"
- Additional dimension: CLINICAL SAFETY — "Could the product cause clinical harm through incorrect information, missed data, or over-reliance?"

**Fintech:**

- REGULATORY: "Banking license required? Money transmission laws? AML/KYC obligations?"
- MOAT: "Network effects from transaction volume? Switching costs from financial integration depth?"
- EXECUTION RISK: "Capital requirements to reach scale? Fraud risk?"

**Marketplace:**

- BUSINESS MODEL: "Chicken-and-egg: which side do you acquire first? How?"
- MOAT: "Network effects — how strong? Local or global?"
- EXECUTION RISK: "Leakage risk — can buyers and sellers go direct after discovery?"

**Enterprise SaaS:**

- MOAT: "Switching costs from integration depth? Data lock-in? Workflow dependency?"
- BUSINESS MODEL: "Land-and-expand path? Seat-based or usage-based?"
- COMPETITION: "Incumbents expanding into your space? Platform risk?"

---

## The Pre-Mortem for Dimension 10

Gary Klein's pre-mortem technique (1998) is the gold standard for execution risk assessment. Instead of asking "what could go wrong?" — which triggers defensive thinking — the pre-mortem asks:

> "Imagine it's one year from now. This company failed. Why?"

This reframe produces more honest answers because:

1. The failure is already a fact (no optimism bias)
2. The question is "why" not "if" (removes the ego protection of "it won't happen to us")
3. It generates specific scenarios, not abstract risks

**Scoring execution risk with pre-mortem:**

1. Ask the pre-mortem question about the vision
2. Generate the top 3-5 failure scenarios
3. For each: assess probability (high/medium/low), impact (fatal/serious/manageable), and detectability (early warning exists / no warning)
4. Score:
   - PASS if all high-probability risks have early detection and mitigation plans
   - CONDITIONAL if risks are identified but mitigation is vague
   - FAIL if founder is unaware of obvious failure modes

**Source:** Klein, G. (2007). "Performing a Project Premortem." _Harvard Business Review_, September 2007.
