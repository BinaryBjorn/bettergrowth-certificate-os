---
name: start-setup
description: Bouwt de volledige GTM-projectstructuur (11 context-docs, CLAUDE.md, input/, output/, specs/) en vult de docs. Detecteert een bestaand masterclass-project (3 docs) en neemt dat werk mee. Use when the user says "start-setup", "start de setup", "zet mijn GTM-systeem op", "set up my GTM context", or opens an empty folder for a new GTM project.
---

# /start-setup — Structuur bouwen + 11 GTM-docs vullen

You are running `/start-setup` for a Better Growth **certificate track** participant. All user-facing text is **Dutch**. Explain what you're doing in plain language; the structure is as much the lesson as the content.

Your job has four phases:

- **Phase 0 — Bestaand project?** Ask the one opening question and pick the path.
- **Phase 1 — Scaffold.** Build the full project structure from the bundled templates.
- **Phase 2 — Intake.** Collect brain dumps + links + files (form in Cowork, chat-intake in Claude Code), or harvest an existing project first and only ask about the gaps.
- **Phase 3 — Build.** Populate the 11 `context/` docs in dependency order with source-of-truth discipline.

## Phase 0 — De openingsvraag: is er al een project?

**Always start here.** Ask (Dutch, one question):

> *"Heb je al een GTM-project met Claude, bijvoorbeeld uit de masterclass? Zo ja: geef me het pad naar die folder (of sleep hem hierheen), dan neem ik alles mee wat je al hebt. Zo nee: dan starten we vers."*

- **Nee / geen project** → Phase 1, then the full intake (Phase 2A).
- **Ja + pad** → Phase 1, then the harvest path (Phase 2B).

If the working folder itself already contains a GTM structure, treat that as the existing project (no path needed) and say so.

## Phase 1 — Scaffold the structure

The scaffold templates live in the `templates/` directory next to this SKILL.md (inside the plugin). They mirror the target structure exactly:

```
templates/
├── CLAUDE.md
├── context/          ← README.md + 11 genummerde docs (01-bedrijf … 11-bezwaren)
├── input/README.md
├── output/README.md
└── specs/README.md
```

> [!important] Scaffold mechanics (learned from a live run)
> Build every scaffold file by **reading the template and writing it with the file tools** (Read + Write). Never copy with bash/`cp`: the plugin's template directories are read-only, so `cp` produces write-protected copies you can't edit later, and mounted working folders may reject bash writes while the file tools work fine.

1. **Inventory the working folder.** Three cases:
   - **Empty (or no GTM structure):** write every template file into the working folder, preserving the folder structure. Tell the user in one line: *"Structuur staat: 11 context-docs, een projectbrein (CLAUDE.md), input/, output/ en specs/."*
   - **Structure already there:** never overwrite. Classify each context doc as **leeg** (only frontmatter, headers, `[TODO]` markers), **deels gevuld**, or **gevuld**. Report the inventory in a short table and only (re)fill docs that are leeg or deels gevuld — and for deels gevuld, only after showing what's there and asking.
   - **Folder contains unrelated files:** fine, build the structure alongside them, but say so.
2. `last-reviewed: TODO` stays TODO until a doc is actually filled (Phase 3 sets it).
3. **Waarschuw bij een sync-folder:** if the working folder lives inside OneDrive/Google Drive/Dropbox, warn that git and sync folders bite each other and recommend a plain local folder (e.g. `~/gtm-os`).

## Phase 2A — Full intake (no existing project)

Collect, per doc, three feeds: a **brain dump**, **links**, and **files**. Any or all; nothing = skip that doc for now.

**In Cowork** (the `mcp__visualize__show_widget` tool is available): render ONE elicitation form per wave (see Waves below) as a single `<form class="elicit">` with one `.elicit-group` per doc: a brain-dump textarea (`data-name="doc{NN}_braindump"`), a links textarea (`data-name="doc{NN}_links"`), and a file dropzone (`data-name="doc{NN}_files"`). The form MUST have the `.elicit-header`, `.elicit-body`, `.elicit-footer` with `.elicit-skip` + `.elicit-submit` buttons (both `type="button"`), inputs named with `data-name` (never `name=`), zero `<script>`/`onclick`. Without the submit button nothing returns. The submission arrives as your next message starting with the form title; verify you received non-empty values before building, and never react to loose file-attachments before the submission line arrives.

**In Claude Code** (no widget tool): run the intake in chat, one doc at a time, dependency order. Per doc: one message with the doc's core question + the three feeds (*"Brain dump? Links? Of drop bestanden in `input/`. Leeg laten = overslaan."*). Keep it brisk: one doc per turn, never re-ask what an earlier answer already covered.

### Waves (don't render 11 questions at once)

- **Wave 1 — Fundament:** 01-bedrijf, 02-diensten, 03-north-star, 04-icp, 05-positionering, 06-kanalen.
- **Wave 2 — Verdieping:** 07-buyer-persona, 08-concurrenten, 09-messaging, 10-proof-points, 11-bezwaren.

Build Wave 1 docs (Phase 3) before offering Wave 2: the verdieping questions are sharper once the foundation exists.

### Core question per doc

| Doc | Kernvraag |
|---|---|
| 01-bedrijf | Wie zijn jullie? (opgericht, grootte, locatie, elevator pitch) |
| 02-diensten | Wat verkopen jullie, aan welke prijs(model)? |
| 03-north-star | Wat is winst dit jaar? Dé metric + je 2-4 prioriteiten |
| 04-icp | Wie is je ideale klant? (een lijst echte klanten is perfect input) |
| 05-positionering | Waarom kiezen klanten jou en niet de rest? |
| 06-kanalen | Waar bereik je die klant vandaag, en wat werkt? |
| 07-buyer-persona | Wie zijn de ménsen die beslissen? Wat drijft hen? |
| 08-concurrenten | Tegen wie verlies je deals, en waarom? |
| 09-messaging | Hoe klink je? Kernboodschap, tone, wat je nooit zegt |
| 10-proof-points | Welk bewijs heb je? (cijfers, testimonials, logo's + toestemming) |
| 11-bezwaren | Waar haken kopers op af, en wat antwoord je? |

## Phase 2B — Harvest path (existing project)

1. **Read the existing project fully**: its context docs (masterclass = `01-bedrijf.md`, `02-klant.md`, `03-positionering.md`), CLAUDE.md, `input/`, and any outputs.
2. **Map the content onto the 11 docs.** The masterclass 3-doc split unpacks like this:
   - `01-bedrijf.md` (oud) → `01-bedrijf` + `02-diensten` + `03-north-star`
   - `02-klant.md` (oud) → `04-icp` + `07-buyer-persona` + `11-bezwaren`
   - `03-positionering.md` (oud) → `05-positionering` + `09-messaging` + `10-proof-points`
   - `06-kanalen` en `08-concurrenten` zijn **altijd nieuw** (zaten niet in de masterclass).
   For a non-masterclass project, map by topic using the source-of-truth table in `context/README.md`.
3. **Fill what you can, mark what you can't.** Populate the 11 docs from the harvested content (Phase 3 discipline applies). Where the old doc is thinner than the new structure, leave `[TODO]`.
4. **Report the harvest** in one table: per doc → `overgenomen` / `deels` / `leeg`.
5. **Then grill the gaps.** For docs that came out `deels` or `leeg`, run the intake (Phase 2A mechanics) **only for those docs**, and ask sharp follow-ups where harvested content is vague or contradictory. Do not re-ask anything the harvest already answered — that wastes the user's head start.

## Phase 3 — Build the docs

Populate in **strict order** (fundament first: 01 → 06, then 07 → 11). The order matters: every doc references the ones above it.

For each doc:

1. **State which doc and why, one sentence** (Dutch, plain language).
2. **Read the doc's template content** — the section structure is the contract; keep it.
3. **Read the upstream docs** this doc references.
4. **Draft from the corpus AND from any reference the user pointed at.** If they gave a reference instead of typed answers — client logos, a website, a deck — **take it from there**: read or research the reference and derive the doc, then show a draft. Only ask what you genuinely cannot infer (one question at a time).
   - Frontmatter: set `last-reviewed:` to today. Keep `authority:`.
   - **For every claim:** check the source-of-truth table in `context/README.md`. If it belongs in another doc, reference it, never duplicate.
   - **Never invent facts.** Ask, or write `[TODO: <wat in te vullen>]`.
5. **Show the draft to the user.** Iterate.
6. **Write the file.**

### Reference-first (icp en concurrenten vooral)

`04-icp.md` is best built *from references*: real customer names or logos ARE the ICP signal — research each account, synthesize the pattern, present a draft. `08-concurrenten.md` likewise: ask for 2-3 names the user loses deals to and research them (Apify/Firecrawl if connected). Confirm only what you truly cannot derive.

## When done

- Set `last-reviewed:` in `context/README.md` to today.
- Recommend, in this order: `/system-audit` to validate, `/understand-me-better` for docs that still feel vague, and **`/bewaar-op-github`** to save the day's work. Day-1 goal of the track: context af én op GitHub.
