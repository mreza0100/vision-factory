# Vision Factory — Installation Wizard

> Follow this checklist to customize vision-factory for your project. Each step has a template you can copy and adapt.

---

## Step 1: Copy into your project

```bash
# Option A: copy (independent, no upstream updates)
cp -r ~/work/skills/vision-factory/.  your-project/.claude/skills/vision-factory/

# Option B: symlink (follows upstream, shared across projects)
ln -s ~/work/skills/vision-factory your-project/.claude/skills/vision-factory
```

If you copied, remove files that belong in the standalone repo only:

```bash
rm -f your-project/.claude/skills/vision-factory/{README.md,LICENSE,.gitignore,INSTALLED.md}
rm -rf your-project/.claude/skills/vision-factory/{profiles,tmp,.git}
```

---

## Step 2: Create the Codex wrapper

Create `.codex/skills/vision-factory/SKILL.md`:

```markdown
---
name: vision-factory
description: "Vision creation, validation, and stress-testing for founders. Three modes: CREATE (Socratic interview → narrative), RESEARCH (cross-check → RRP), STRESS-TEST (hybrid rubric). General-purpose protocol — consumer commands add domain-specific context."
---

# Vision Factory — Codex Wrapper

> Claude and Codex mirror the same Professor contract. This wrapper gives Codex runtime mechanics for the vision-factory skill.

## Role Manual

Read and follow the full protocol at `.claude/skills/vision-factory/SKILL.md`. That is the source of truth for all three modes (CREATE, RESEARCH, STRESS-TEST), scoring rubric, and artifact formats.

## Codex-Specific Rules

- **RRP output:** Mode B produces a research prompt (RRP), not inline research.
- **Artifact location:** Save artifacts where the consuming command specifies. Default to `tmp/`.
- **Voice profiles:** Check `.claude/skills/ghostwriter/profiles/` for applicable voice profiles.
- **Domain context:** The consuming command provides domain-specific reference docs. Read them before each mode.
```

**Customize:** If your project has a domain overlay (see Step 5), add a line noting it's always-on.

---

## Step 3: Add to CLAUDE.md Skills table

Add this row to your project's Skills table:

```markdown
| `vision-factory` | "vision", "create a vision", "stress-test my vision" — Socratic interview → narrative → cross-check RRP → hybrid rubric scoring |
```

**Customize:** Adjust the trigger description if you added domain-specific triggers or changed the rubric description (e.g., "enterprise SaaS rubric" instead of "hybrid rubric scoring").

---

## Step 4: Wire into a consumer command

The most natural consumer is `/mentor`. Add this section to your mentor command file (`.claude/commands/mentor.md`), just before the Rules section:

```markdown
## Vision Factory — Vision Creation & Stress-Testing

When the founder needs to create, validate, or pressure-test a vision, load the **vision-factory skill** (`.claude/skills/vision-factory/SKILL.md`).

**Project-specific hooks:**

- **Before Mode A (CREATE):** Read `{YOUR_STRATEGY_DOC}` for market context. Read `{YOUR_COMPETITIVE_DOC}` for competitor landscape.
- **Before Mode B (RESEARCH):** Read `{YOUR_COMPETITIVE_DOC}` and `{YOUR_STRATEGY_DOC}` for the cross-check. These are the "available knowledge" that Mode B references.
- **Before Mode C (STRESS-TEST):** Read all mentor reference docs. Ground REGULATORY, COMPETITION, and BUSINESS MODEL dimensions in your knowledge base.
- **Artifact location:** Save to the active epic dir (`docs/epics/{name}/`) if an epic is active, otherwise `{YOUR_DEFAULT_LOCATION}`.
- **Voice:** Run Mode A narrative and Mode C hardened vision through ghostwriter with `{YOUR_PROFILE}.md` profile.

**Trigger:** When `$ARGUMENTS` includes `vision`, `vision-factory`, "create a vision", "stress-test", or "pressure-test".
```

**Replace the placeholders:**

| Placeholder               | What to put                                        | Example                                           |
| ------------------------- | -------------------------------------------------- | ------------------------------------------------- |
| `{YOUR_STRATEGY_DOC}`     | Path to your startup/market strategy reference doc | `$CDOCS/mentor/$REFS/startup-strategy.md`         |
| `{YOUR_COMPETITIVE_DOC}`  | Path to your competitive intelligence doc          | `$CDOCS/mentor/$REFS/competitive-intelligence.md` |
| `{YOUR_DEFAULT_LOCATION}` | Where vision artifacts land when no epic is active | `docs/business/` or `tmp/`                        |
| `{YOUR_PROFILE}`          | Ghostwriter profile name for narrative output      | `paul-graham` or a custom project profile         |

---

## Step 5: Add a domain-specific rubric overlay (optional but recommended)

If your project operates in a specific domain, add an overlay table to the SKILL.md inside Mode C, after the ten dimensions. This adds sub-questions without changing the core rubric.

### Template

Add this section inside Mode C of your project's `.claude/skills/vision-factory/SKILL.md`, after the ten dimensions and before "### Scoring":

```markdown
### {Your Domain} Overlay

{One sentence: why this overlay exists.}

| Dimension      | Additional sub-question                  | Why      |
| -------------- | ---------------------------------------- | -------- |
| MARKET         | "{domain-specific market question}"      | {reason} |
| PROBLEM        | "{domain-specific pain question}"        | {reason} |
| REGULATORY     | "{domain-specific regulatory question}"  | {reason} |
| MOAT           | "{domain-specific moat question}"        | {reason} |
| COMPETITION    | "{domain-specific competition question}" | {reason} |
| EXECUTION RISK | "{domain-specific risk question}"        | {reason} |
```

### Ready-made overlays

**Health-tech:**

```markdown
### Health-Tech Overlay

Clinical data, patient safety, and regulatory certification shape every dimension.

| Dimension      | Additional sub-question                                                                 | Why                                         |
| -------------- | --------------------------------------------------------------------------------------- | ------------------------------------------- |
| REGULATORY     | "Does the product touch patient data? HIPAA/GDPR compliance addressed?"                 | Health data is sacred ground                |
| REGULATORY     | "Clinical certifications required? (MDR, NEN 7510, ISO 13485)"                          | Certification timelines affect go-to-market |
| MOAT           | "Does usage generate clinical data that improves the product?"                          | Data moat from clinical depth               |
| PROBLEM        | "Is the pain clinical (affects outcomes), administrative (affects workflows), or both?" | Determines buyer and user                   |
| COMPETITION    | "Do competitors have clinical validation studies? Do you?"                              | Evidence bar in health-tech                 |
| EXECUTION RISK | "Could the product cause clinical harm through incorrect or missing information?"       | Patient safety is non-negotiable            |
```

**Enterprise SaaS:**

```markdown
### Enterprise SaaS Overlay

Procurement, tenant isolation, and integration depth shape every dimension.

| Dimension      | Additional sub-question                                                                                | Why                                           |
| -------------- | ------------------------------------------------------------------------------------------------------ | --------------------------------------------- |
| MARKET         | "Is the buyer a team lead, VP, or C-level? Who holds budget?"                                          | Enterprise sales cycle depends on buyer level |
| PROBLEM        | "Is the pain felt by the user (employee) or the buyer (leader)? Are they the same?"                    | Enterprise adoption needs both                |
| SOLUTION FIT   | "Does the solution survive a security review and procurement process?"                                 | Enterprise deals die in procurement           |
| MOAT           | "Does usage generate proprietary data that deepens with time? Switching costs from integration depth?" | Enterprise stickiness                         |
| BUSINESS MODEL | "Land-and-expand path? Seat-based, usage-based, or workflow-based pricing?"                            | Enterprise pricing model                      |
| REGULATORY     | "SOC2/ISO 27001 requirements? Tenant isolation? Data residency?"                                       | Enterprise security table stakes              |
| COMPETITION    | "Incumbent response: can the platform players add this feature?"                                       | Platform risk                                 |
| EXECUTION RISK | "Implementation complexity: how long from signed contract to value?"                                   | Enterprise onboarding drag                    |
```

**Fintech:**

```markdown
### Fintech Overlay

Licensing, financial controls, and fraud risk shape every dimension.

| Dimension      | Additional sub-question                                                   | Why                                    |
| -------------- | ------------------------------------------------------------------------- | -------------------------------------- |
| REGULATORY     | "Banking license required? Money transmission laws? AML/KYC obligations?" | Regulatory is make-or-break in fintech |
| MOAT           | "Network effects from transaction volume? Regulatory barriers to entry?"  | Fintech moats are often regulatory     |
| BUSINESS MODEL | "Transaction-based, subscription, or hybrid? Interchange or markup?"      | Unit economics vary wildly by model    |
| EXECUTION RISK | "Capital requirements to reach scale? Fraud risk?"                        | Fintech burns cash before it earns it  |
| COMPETITION    | "Incumbent banks adding this capability? Stripe/Plaid platform risk?"     | Platform risk in fintech is real       |
```

**Marketplace:**

```markdown
### Marketplace Overlay

Liquidity, chicken-and-egg dynamics, and leakage risk shape every dimension.

| Dimension      | Additional sub-question                                                   | Why                                   |
| -------------- | ------------------------------------------------------------------------- | ------------------------------------- |
| BUSINESS MODEL | "Chicken-and-egg: which side do you acquire first? How?"                  | The classic marketplace blocker       |
| MOAT           | "Network effects — how strong? Local or global? Same-side or cross-side?" | Marketplace moats are network effects |
| EXECUTION RISK | "Leakage risk — can buyers and sellers go direct after discovery?"        | Disintermediation kills marketplaces  |
| MARKET         | "Supply-constrained or demand-constrained? Which side is harder to get?"  | Determines go-to-market strategy      |
```

---

## Step 6: Verify

Run this checklist after installation:

```bash
# Skill file exists
ls .claude/skills/vision-factory/SKILL.md

# Codex wrapper exists
ls .codex/skills/vision-factory/SKILL.md

# CLAUDE.md table has the entry
grep "vision-factory" CLAUDE.md

# Mentor references it
grep "vision-factory" .claude/commands/mentor.md

# Trigger works
# Run: /mentor vision
```

---

## Quick Reference

| What               | Where                                                                              |
| ------------------ | ---------------------------------------------------------------------------------- |
| Core protocol      | `.claude/skills/vision-factory/SKILL.md`                                           |
| Codex wrapper      | `.codex/skills/vision-factory/SKILL.md`                                            |
| Skills table entry | `CLAUDE.md` § Skills                                                               |
| Consumer hooks     | `.claude/commands/mentor.md` § Vision Factory                                      |
| Domain overlay     | Inside SKILL.md § Mode C, after the ten dimensions                                 |
| Artifact output    | Epic dir, `docs/business/`, or `tmp/`                                              |
| Voice profile      | `.claude/skills/ghostwriter/profiles/{name}.md`                                    |
| Standalone repo    | [github.com/mreza0100/vision-factory](https://github.com/mreza0100/vision-factory) |
