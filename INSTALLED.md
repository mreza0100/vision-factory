# Vision Factory — Install Notes

## What this skill is

Single-purpose. PG-grounded. No multi-profile abstraction.

If you came here looking for the v1 multi-profile / consumer-integration / domain-overlay scaffolding — it's gone. v2 is one opinionated thing: PG's vision filters, operationalized.

## Install

```bash
# Copy into your project's skill directory
cp -r ~/work/skills/vision-factory/. your-project/.claude/skills/vision-factory/

# Or symlink (follows upstream)
ln -s ~/work/skills/vision-factory your-project/.claude/skills/vision-factory
```

If you copied, you can remove files that belong in the standalone repo only:

```bash
rm -f your-project/.claude/skills/vision-factory/{README.md,LICENSE,.gitignore,INSTALLED.md}
rm -rf your-project/.claude/skills/vision-factory/.git
```

The skill loads only the curated `references/pg-*.md` distillations at runtime. No external corpus is needed at install time.

## Trigger

The skill loads on any of these phrases (full list in SKILL.md frontmatter):

- `vision`, `vision-factory`
- "create a vision", "build a vision", "write a vision", "draft a vision"
- "stress-test my vision", "pressure-test", "challenge my vision"
- "validate my vision", "research my vision", "cross-check"
- "vision for X", "north star for X", "one-pager for X"
- "founding narrative", "origin story", "why now for X"

## Mode B notes

Mode B (RESEARCH) executes research itself via the `RR` skill (or whatever research pipeline is in the project). It does NOT hand the user an intermediate prompt to run. If the project doesn't have `RR` or an equivalent, Mode B falls back to whatever research tools are available — but never asks the user to run something manually.

## Artifact location

By default, vision artifacts (`vision-draft.md`, `vision-research.md`, `vision-scorecard.md`) land wherever the user specifies. If unspecified, default to `tmp/` in the working directory.

## What v2 removed from v1

- Multi-profile scaffolding (`profiles/` is now empty, kept only for git compatibility)
- Generic VC framework references (Christensen, Helmer 7 Powers, Sequoia, Andreessen) — replaced with PG essays
- Domain-specific overlays (health-tech, fintech, marketplace, enterprise SaaS) — if you need them, layer them in a consuming command, not here
- Voice-profile hooks — the voice is PG's, baked in
- Codex wrapper instructions, Claude.ai-specific install steps, consumer-command integration templates

If any of these matter for your project, fork v1 (it's still in git history). v2 is the focused thing.
