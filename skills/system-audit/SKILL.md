---
name: system-audit
description: Read-only audit van het GTM-systeem. Checkt frontmatter, gebroken links, duplicatie tegenover de bron-van-waarheid-docs, verouderde last-reviewed datums, en of specs en gebouwde skills nog kloppen. Rapporteert alleen, past nooit iets aan. Use when the user says "system-audit", "audit mijn context", "check mijn systeem", "klopt alles nog", or before calling the context done.
---

# /system-audit — Systeem-audit (read-only)

You are running `/system-audit`. Your job: validate the whole GTM project against its modular discipline and produce a clear report. **You never write or edit files.** If the user wants fixes after the report, guide them or let them ask explicitly.

The user is a Better Growth certificate track participant. Report in **Dutch**, plain language.

## Setup

1. **Locate the folders**: `context/`, `specs/`, `.claude/skills/`, `input/`, `output/`, `CLAUDE.md`.
2. **Read `context/README.md`** — load the source-of-truth table and the modularity rule.
3. **Inventory all markdown files** in the project.

## Zes checks (run all, report all)

### Check 1 — Frontmatter

For each `.md` in `context/`: `title:`, `description:` (≤200 chars), `last-reviewed:` (valid date; a leftover `TODO` = never filled), `refresh-cadens:`, and `authority:` on the source-of-truth docs per the README table.

### Check 2 — Gebroken links

Scan every `[text](path)` link in every file, resolve relative to the file, verify the target exists. Report file + line + link text.

### Check 3 — Verouderd

Compare `last-reviewed` vs `refresh-cadens` (`jaarlijks` → stale >365d; `per kwartaal` → stale >95d). Sort oldest first.

### Check 4 — Duplicatie tegenover bron van waarheid (belangrijkste check)

For each source-of-truth doc: pick 3-5 distinctive phrases/facts, grep all OTHER files for them. Found with substantive context elsewhere? Flag as potential duplication. `output/` files are snapshots — flag as "review", not "violation". Be conservative; false positives waste time.

### Check 5 — Skeletten

Docs with only frontmatter + headers + `[TODO]` markers: scaffolded but never filled.

### Check 6 — Specs ↔ skills (nieuw in de certificate track)

Cross-check `specs/skill-plan.md`, the `specs/spec-*.md` files, and `.claude/skills/`:

- **Gebouwde skill zonder spec** → note it ("werkt prima, maar zonder spec is hij later moeilijker te onderhouden; een korte spec achteraf kan"). Zacht signaal, geen violation.
- **Spec op `gespecced` zonder gebouwde skill** → staat hij nog op de planning of is hij stilletjes gestorven?
- **Status in `skill-plan.md` klopt niet met de realiteit** (bv. skill bestaat maar status is `gepland`) → flag with the correct status.
- **Skill-plan ontbreekt terwijl er wel skills zijn** → recommend one `/understand-me-better` run to create it.

## Output format

```markdown
# Systeem-audit — <YYYY-MM-DD>

## Samenvatting
- Bestanden gescand: N
- Frontmatter-issues: N · Gebroken links: N · Verouderd: N
- Duplicatie-kandidaten: N · Skeletten: N · Specs ↔ skills: N

## 1. Frontmatter
<tabel of "Niets gevonden.">

## 2. Gebroken links
<tabel of "Niets gevonden.">

## 3. Verouderd
<tabel, oudste eerst, of "Niets gevonden.">

## 4. Duplicatie tegenover bron van waarheid
<tabel of "Niets gevonden." — onderscheid "violation" en "review">

## 5. Skeletten
<lijst of "Alles gevuld.">

## 6. Specs ↔ skills
<tabel of "Plan, specs en skills lopen gelijk.">

## Aanbevolen volgende stappen
<3-5 geprioriteerde acties, bv. "Run /understand-me-better op 05-positionering", "Zet skill X in skill-plan.md op gebouwd.">
```

## Discipline reminders

- **No writes. No edits.** Pure reporting.
- Every flag includes file path + line + concrete suggestion.
- If the system is healthy, say so plainly. Don't manufacture findings.
