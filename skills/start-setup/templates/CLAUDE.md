# GTM-OS — Projectbrein

Je werkt aan het modulaire go-to-market systeem van **het bedrijf van de gebruiker**. De gebruiker is deelnemer van de Better Growth certificate track en bouwt hier een systeem waar AI heel goed op kan werken: context + structuur + eigen skills.

## De ene regel die telt

**Eén bron van waarheid per onderwerp. Elk ander doc verwijst via een markdown-link, en herhaalt nooit.**

De volledige bron-van-waarheid-tabel staat in `context/README.md`. Lees die voor je schrijft.

## Mappen

- `context/` — de 11 GTM-docs (genummerd). Bron van waarheid voor alles wat GTM is.
- `input/` — ruw materiaal dat de gebruiker binnenbrengt: websiteteksten, decks, transcripts, klantinterviews, screenshots. **Lees hieruit bij het vullen van context.** Bewerk nooit bestanden in `input/`.
- `output/` — gegenereerde deliverables: campagnebriefs, salesscripts, landingsteksten, advertentievarianten. **Schrijf deliverables hier.** Elk output-bestand verwijst naar de `context/`-docs waarop het steunt.
- `specs/` — het skill-plan en de specs. `specs/skill-plan.md` is het master-overzicht van alle skills die de gebruiker wil bouwen (met status). Per skill komt er een `specs/spec-<naam>.md` vóór hij gebouwd wordt.
- `.claude/skills/` — de skills die de gebruiker zelf bouwt.

## Skills

- `/start-setup` — bouwt deze structuur en vult de 11 `context/`-docs (ook vanuit een bestaand masterclass-project).
- `/understand-me-better` — de universele grill: scherpt context aan, maakt van een skill-plan `specs/skill-plan.md`, en schrijft per skill-idee een spec.
- `/system-audit` — read-only check: structuur, verwijzingen, duplicatie, veroudering, specs ↔ skills.
- `/bewaar-op-github` — bewaart het project in een privé GitHub-repo. Het einde van elke werksessie.

## De skill-werklus (zachte regel)

Wanneer de gebruiker een **nieuwe skill wil bouwen**, stel dan voor om eerst `/understand-me-better` te draaien zodat er een spec ligt in `specs/` en `specs/skill-plan.md` wordt bijgewerkt. **Stel het voor, dwing het nooit af.** Wil de gebruiker meteen bouwen, dan bouw je meteen; noteer hoogstens achteraf een korte spec.

Een skill is een **werkwijze-skill** (vaste stappen, Claude volgt de route) of een **kennis-skill** (regels en een kwaliteitslat, Claude kiest de route). Bouw hem in de vorm van zijn soort; de spec zegt welke.

Statussen in `specs/skill-plan.md`: `gepland` → `gespecced` → `gebouwd` → `getest`. Werk de status bij wanneer een stap gezet is.

## De contextmeter-nudge (zacht)

Elke context-doc heeft een `status:` in de frontmatter (leeg / ontwerp / deels / gevuld). Bij het begin van betekenisvol werk: staan er fundament-docs (01 t/m 05) nog niet op `gevuld`, meld dat dan één keer, in één regel: *"Contextmeter: 7/11 · grootste gat: north-star. Wil je die eerst vullen?"* Maximaal één nudge per sessie. **Nooit blokkeren**: wil de gebruiker doorwerken, werk door. Outputs die op een `ontwerp`- of `leeg`-doc steunen mogen dat in één zin vermelden.

## Werkregels

- **Lees `context/README.md` eerst** bij elk niet-trivialer werk.
- **Heb je informatie nodig?** Check `input/` voor je het vraagt. De gebruiker heeft het misschien al aangeleverd.
- **Verzin nooit** feiten over het bedrijf van de gebruiker. Weet je het niet: vraag het, of schrijf `[TODO: <wat in te vullen>]`.
- **Dupliceer nooit** inhoud uit een bron-van-waarheid-doc. Verwijs met een markdown-link.
- **Zet `last-reviewed:`** op vandaag bij elke aanpassing.
- Elke `.md` in `context/` heeft frontmatter: `title`, `description`, `last-reviewed`, `refresh-cadens`, en op bron-van-waarheid-docs ook `authority`.
- Na betekenisvol werk: herinner de gebruiker aan `/bewaar-op-github`.

## Bij het genereren van output

- Elk output-bestand opent met één zin: *"Gegenereerd op <datum> op basis van <de gebruikte context/-docs>."*
- Trek uit `context/` via verwijzing, niet via kopie.
- Bestandsnamen als `output/2026-Q3-campagnebrief.md` of `output/landing-hero-varianten.md`.

## Voor je positionering of andere claims aanpast

1. Lees het bron-van-waarheid-doc volledig.
2. Leg de voorgestelde wijziging aan de gebruiker voor. Pas nooit stilzwijgend aan.
3. Check daarna welke andere docs naar de gewijzigde passage verwijzen.

## Pedagogische noot

Dit project leert de gebruiker Claude Code gebruiken ÉN een modulair GTM-systeem onderhouden. Maak bij vragen de architectuur zichtbaar: leg uit welk doc het onderwerp bezit en waarom, in plaats van alleen stil een bestand te bewerken. De structuur is evenzeer de les als de inhoud.
