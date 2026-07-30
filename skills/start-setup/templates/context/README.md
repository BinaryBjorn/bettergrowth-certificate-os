---
title: GTM Context — Index
description: Bron-van-waarheid-tabel, modulariteits-regel en navigatie voor de 11 GTM context-docs. Lees dit voor je iets vult.
last-reviewed: TODO
refresh-cadens: per kwartaal
---

# GTM Context

> Modulaire go-to-market context voor **<jouw bedrijf>**. Vul de docs hieronder met `/start-setup`. Scherp aan met `/understand-me-better`. Valideer met `/system-audit`. Bewaar met `/bewaar-op-github`.

## Mappenkaart

```
context/
├── README.md              ← dit bestand
│
├── 01-bedrijf.md          ← wie jullie zijn (feitelijke basis)
├── 02-diensten.md         ← wat jullie verkopen
├── 03-north-star.md       ← dé metric + KPI's + prioriteiten
├── 04-icp.md              ← aan wie jullie verkopen + buying committee
├── 05-positionering.md    ← kernpositie + differentiators
├── 06-kanalen.md          ← waar je de ICP bereikt
├── 07-buyer-persona.md    ← diep op de mensen binnen de ICP
├── 08-concurrenten.md     ← wie er nog in het gesprek zit
├── 09-messaging.md        ← hoe je erover praat
├── 10-proof-points.md     ← bewijs achter de claims
└── 11-bezwaren.md         ← waar kopers op afhaken + antwoorden
```

## Bron-van-waarheid-tabel

| Onderwerp | Bron van waarheid |
|---|---|
| Bedrijfsidentiteit, feiten, leiderschap | [`01-bedrijf.md`](01-bedrijf.md) |
| Dienstenportfolio, capabilities, pricing | [`02-diensten.md`](02-diensten.md) |
| Primaire metric, KPI's, strategische prioriteiten | [`03-north-star.md`](03-north-star.md) |
| ICP-definitie, buying committee, tiers | [`04-icp.md`](04-icp.md) |
| Positioneringsstatement, differentiators | [`05-positionering.md`](05-positionering.md) |
| Kanalenoverzicht + rol per kanaal | [`06-kanalen.md`](06-kanalen.md) |
| Buyer persona's (diep) | [`07-buyer-persona.md`](07-buyer-persona.md) |
| Concurrenten (direct + indirect) | [`08-concurrenten.md`](08-concurrenten.md) |
| Messaging (per funnel-fase, voice-ankers) | [`09-messaging.md`](09-messaging.md) |
| Proof points, testimonials, claims-discipline | [`10-proof-points.md`](10-proof-points.md) |
| Bezwaren + antwoorden | [`11-bezwaren.md`](11-bezwaren.md) |

## De modulariteits-regel (de ene regel die telt)

> **Bron van waarheid op één plek. Overal elders: verwijzen, nooit dupliceren.**

Voor elke claim, lijst, definitie, cijfer of tabel:

1. **Zoek de bron van waarheid** in de tabel hierboven.
2. **Het bronbestand** bezit de inhoud volledig (en heeft een `authority:`-lijn in de frontmatter).
3. **Elk ander bestand** dat het onderwerp nodig heeft, gebruikt een markdown-link, geen herhaling.

### ✅ WEL zo

- *"Onze primaire persona is de IT-manager (zie [`07-buyer-persona.md`](07-buyer-persona.md))."*
- *"Mid-market (gedefinieerd in [`04-icp.md`](04-icp.md)) is onze focus voor 2026."*

### ❌ NIET zo

- ❌ De pijnpunten van de IT-manager herhalen in `09-messaging.md`.
- ❌ "Mid-market = 200-2000 FTE" op drie plaatsen definiëren.

### De drift-test

Bij elke claim die je schrijft: *"Als dit verandert in het bronbestand, moet ik het hier dan ook aanpassen?"*

- **Ja** → je dupliceert. Vervang door een verwijzing.
- **Nee** → functioneel gebruik van de claim, prima.

## Vul-volgorde

`/start-setup` loopt de docs in deze volgorde, en respecteer ze ook als je handmatig vult:

**Fundament (eerst, in deze volgorde — ze ontsluiten de rest):**

1. `01-bedrijf.md`
2. `02-diensten.md`
3. `03-north-star.md`
4. `04-icp.md`
5. `05-positionering.md`
6. `06-kanalen.md`

**Daarna (aanbevolen volgorde):**

7. `07-buyer-persona.md`
8. `08-concurrenten.md`
9. `09-messaging.md`
10. `10-proof-points.md`
11. `11-bezwaren.md`

De volgorde telt: elk doc verwijst naar de docs erboven. Bedrijf en diensten zijn de feitelijke basis; je hebt je ICP nodig voor je kan positioneren; goede messaging kan pas als er positionering is om naar te wijzen.

## Frontmatter-conventie

Elk doc heeft:

```yaml
---
title: <naam>
description: <één zin>
last-reviewed: <YYYY-MM-DD>
refresh-cadens: <jaarlijks / per kwartaal>
authority: "<alleen op bron-van-waarheid-docs — welk onderwerp dit bestand bezit>"
---
```

`/start-setup` zet deze voor je. `/system-audit` controleert ze.

---

**Volgende stap:** run `/start-setup` om te beginnen.
