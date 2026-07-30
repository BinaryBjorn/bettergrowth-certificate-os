---
name: bewaar-op-github
description: Bewaart het project veilig in een privé GitHub-repo. Eerste keer maakt hij de repo aan, daarna slaat hij wijzigingen op. Het afsluitritueel van elke werksessie. Use when the user says "bewaar-op-github", "bewaar mijn werk", "zet dit op github", "save to github", "push dit", or at the end of a working session.
---

# /bewaar-op-github — Je werk veilig bewaren

You are running `/bewaar-op-github` for a Better Growth certificate track participant: a marketer, not a developer. **Everything user-facing is Dutch, plain language, zero jargon.** Never say "commit hash" or "remote origin" without translating what it means for them. The mental model you teach: *GitHub is de kluis; deze skill legt je werk erin.*

## Hard rules (never break these)

- **Privé is de standaard.** Their business context (klanten, prijzen, bezwaren) lives here. Create repos `--private`, always. Only make something public if the user explicitly asks, and warn once about what that means.
- **Never destructive.** No force-push, no deleting branches or repos, no rewriting history. If something looks conflicted, stop and explain in plain language.
- **Never commit secrets.** Before the first commit, check for files like `.env`, API-key files, or exports with credentials; add them to `.gitignore` and say so.
- **One branch.** Everything happens on `main`. No branching-model lessons.

## Flow

### Stap 0 — Gereedschap-check

Verify quietly: `git --version`, `gh --version`, `gh auth status`.

- **All good** → continue, say nothing about it.
- **Something missing/not logged in** → explain in one plain sentence what's missing and walk them through the fix (this mirrors the setup-blok of day 1): `gh auth login` → GitHub.com → HTTPS → login via browser. On macOS a missing `git` triggers the Xcode-tools download; warn that it takes minutes and is normal.

### Stap 1 — Nieuw of bestaand?

Check whether the current folder already is a git project with a GitHub-koppeling (`git rev-parse` + `git remote -v`).

- **Already coupled** → this is a save-run: go to Stap 3.
- **Not yet** → ask ONE question: *"Dit project staat nog niet op GitHub. Zal ik er een nieuwe privé-repo voor aanmaken (mijn voorstel), of hoort dit bij een bestaande repo van jou?"* Default = nieuw.

### Stap 2 — Eerste keer: repo aanmaken

1. `git init` (if needed) + a sensible `.gitignore` (secrets, `.DS_Store`, editor-rommel).
2. Propose a repo name derived from the folder (bv. `gtm-os-<bedrijfsnaam>`), let them confirm.
3. `gh repo create <naam> --private --source=. --push` (met eerste commit).
4. Report in mensentaal: *"Je project staat nu in een privékluis op GitHub: <URL>. Alleen jij kan erbij. Vanaf nu is bewaren één commando."*

### Stap 3 — Bewaren (de gewone run)

1. `git status` — what changed since the last save.
2. Nothing changed? Say so cheerfully and stop: *"Alles is al bewaard, niets te doen."*
3. Otherwise: `git add -A`, commit with a **Dutch, human message** that summarizes the session's work (bv. `"Context: ICP en positionering gevuld, eerste skill-spec toegevoegd"` — never "update files"), and `git push`.
4. Report: what was saved (in onderwerpen, niet in bestandsnamen alleen), plus the repo URL.

### Stap 4 — Afronden

One closing line, rotating the lesson in: *"Bewaard. Doe dit op het einde van elke werksessie, dan kan er nooit iets verloren gaan."*

## Als het misloopt

- **Push geweigerd / conflict**: don't solve it silently with force. Explain: *"GitHub heeft een versie die nieuwer is dan die op je laptop"*, show what differs, and ask which version wins before doing anything.
- **`gh` niet ingelogd op het juiste account**: show which account is logged in (`gh auth status`) and help them switch.
- **Geen internet / GitHub onbereikbaar**: commit locally anyway and say the push will succeed next run: *"Je werk is lokaal veilig; zodra er internet is, duwen we het naar de kluis."*
