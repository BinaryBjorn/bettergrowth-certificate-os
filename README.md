# Better Growth Certificate OS

De plugin van de Better Growth **Certificate Track: AI-driven growth**. Bouw een volledig GTM-systeem met Claude Code: 11 context-docs, een specs-workflow voor je eigen skills, en GitHub-backup.

## Installeren

In Claude Code (of Cowork):

```
/plugin marketplace add BinaryBjorn/bettergrowth-certificate-os
```

en installeer daarna de plugin `certificate-os`.

## De vier skills

| Skill | Wat hij doet |
|---|---|
| `/start-setup` | Bouwt de volledige projectstructuur (11 context-docs, CLAUDE.md, input/, output/, specs/) en vult de docs. Heb je al een masterclass-project met de 3 docs? Geef het pad en hij neemt je werk mee. |
| `/understand-me-better` | De universele grill. Leg hem je business voor en hij scherpt je context-docs aan. Leg hem je skill-plan voor en hij schrijft `specs/skill-plan.md`. Leg hem één skill-idee voor en hij bepaalt eerst of het een werkwijze-skill (vaste stappen) of een kennis-skill (regels en kwaliteitslat) wordt, en schrijft er dan een spec voor. |
| `/system-audit` | Read-only check van het hele systeem: frontmatter, verwijzingen, duplicatie, veroudering, en of je specs en skills nog kloppen. |
| `/bewaar-op-github` | Bewaart je project in een **privé** GitHub-repo. Eerste keer: repo aanmaken. Daarna: wijzigingen opslaan. Het afsluitritueel van elke werksessie. |

## Updates ophalen

Claude ververst een plugin **niet vanzelf**. Een nieuwe versie binnenhalen gaat in twee stappen, daarna herstart je Claude Code.

1. Haal de nieuwe versie van de marketplace op:

   ```
   /plugin marketplace update bettergrowth-certificate
   ```

2. Werk de geïnstalleerde plugin bij. Typ `/plugin`, open de geïnstalleerde plugin `certificate-os` en kies bijwerken. Of in een terminal:

   ```
   claude plugin update certificate-os@bettergrowth-certificate
   ```

3. Herstart Claude Code (of open een nieuw venster). Pas dan werkt de nieuwe versie.

Welke versie je hebt, zie je met `claude plugin list`.

## Voor wie

Deelnemers van de Better Growth Certificate in AI-Driven Growth. Voorkennis: de masterclass "Accelereer je groei met Claude" of vlot met Claude kunnen werken.
