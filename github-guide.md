# Jak pracujeme s GitHubem

Veškerý kód žije v naší GitHub organizaci **codetogodmode**. Tady je všechno, co potřebuješ vědět.

## Kde co žije

Organizace má několik typů repozitářů:

- **member-{jméno}** — tvůj hlavní learning repo, projekty ve složkách (src/Calculator/, src/ZooManager/...). Vytváří Martin na začátku akademie.
- **sandbox-{jméno}-*** — tvůj osobní sandbox pro experimenty a PoC (vytvoříš si sám přes bota)
- **capstone-{jméno}-*** — tvůj hlavní projekt (od Layer 3 dál, vytváří Martin)
- **challenge-{jméno}-*** — gate challenge zadání (vytváří Martin)
- **shared-*** — společné projekty, na kterých pracujeme všichni (Layer 1-2)
- **demo-*** — ukázkový kód ze sessions
- **template-*** — startovní šablony, ze kterých se tvoří nové projekty
- **handbook** — pravidla, dokumenty, návody (tohle čteš právě teď)
- **study-book** — učební materiály ze sessions

## Jak vytvořit nové repo

### Sandbox (sám, kdykoliv)
Pro experimenty, PoC, cvičení — na Discord serveru v kanálu **#repos** napiš:
```
/new-repo název: muj-pokus template: console
```
Bot vytvoří `sandbox-{tvoje-jméno}-muj-pokus` v organizaci. Na výběr máš template `console`, `webapi`, nebo `empty` (prázdné repo). Limit: 25 sandbox repos.

### Member / Capstone / Challenge / Shared / Demo (Martin)
Member repos (`member-{jméno}`) vytváří Martin na začátku akademie -- každý member dostane svůj repo se strukturou pro projekty. Capstone projekty, gate challenges, shared a demo repos taky zakládá Martin -- řekni mu co potřebuješ a on to založí se správným nastavením.

## Jak začít s repem

### 1. Klonování

```bash
git clone https://github.com/codetogodmode/NAZEV-REPA.git
cd NAZEV-REPA
```

### 2. Vytvoř branch

Nikdy nepracuj přímo na `main`. Vždy si vytvoř branch:

```bash
git checkout -b feature/popis-co-delas
```

**Pojmenování branchí:**
- `feature/login-formular` — nová funkce
- `fix/oprava-kalkulacky` — oprava bugu
- `refactor/rozdeleni-tridy` — refaktoring

**Špatné názvy:**
- `moje-zmeny`, `test`, `asdf`, `branch1`

### 3. Pracuj a commituj

Dělej malé, logické commity. Každý commit = jedna ucelená změna.

```bash
git add src/Calculator.cs
git commit -m "Add division method to Calculator"
```

**Dobrý commit message:**
- `Add user input validation`
- `Fix division by zero crash`
- `Refactor Calculator into separate methods`

**Špatný commit message:**
- `update`, `fix`, `stuff`, `asdf`, `změny`

Commit message piš anglicky — je to standard v celém sw světě.

### 4. Pushni branch

```bash
git push origin feature/popis-co-delas
```

Pokud pushneš poprvé, Git ti řekne přesný příkaz — stačí ho zkopírovat.

### 5. Otevři Pull Request

1. Jdi na GitHub → tvůj repo → uvidíš banner "Compare & pull request" → klikni
2. Vyplň PR template:
   - **Co se změnilo** — co tvůj kód dělá
   - **Jak to ověřit** — jak poznat že to funguje
   - **Bezpečnost** — odškrtni že v kódu nejsou secrets
   - **AI disclosure** — jestli ti pomáhala AI a jak
3. Klikni "Create pull request"

### 6. Code review

Martin (nebo Matěj) se podívá na tvůj kód a buď:
- **Approve** — kód je OK, můžeš mergnout
- **Request changes** — něco je potřeba opravit

Pokud máš request changes:
1. Přečti komentáře
2. Oprav co je potřeba (na stejném branchi)
3. Commitni a pushni opravu
4. PR se automaticky updatne

**Nebuď nervózní z review.** Každý dostává feedback — i senioři. Review není kritika, je to spolupráce.

### 7. Merge

Až máš approval:
1. Klikni "Merge pull request" na GitHubu
2. Smaž branch (GitHub to nabídne)
3. Lokálně se vrať na main:

```bash
git checkout main
git pull
```

## Issues

Issues jsou úkoly — co je potřeba udělat.

**Jak vytvořit issue:**
1. V repu → Issues → New Issue
2. Vyber template (Task, Bug, nebo Blocked)
3. Vyplň popis a acceptance criteria

**Jak pracovat s issue:**
1. Přiřaď si ho (Assignees → vyber sebe)
2. Vytvoř branch pojmenovaný podle issue: `feature/42-login-formular`
3. V commit message nebo PR popisu napiš `Closes #42` — issue se automaticky zavře po merge

## Co NEDĚLAT

- **Nepushuj na main** — vždy přes branch + PR
- **Nepoužívej force push** (`git push --force`) — zničí historii
- **Necommituj secrets** — API klíče, hesla, tokeny. Viz [Secrets Guide](secrets-guide.md)
- **Necommituj bez popisu** — `git commit -m "stuff"` je k ničemu
- **Neignoruj review** — pokud nesouhlasíš s komentářem, diskutuj, neignoruj
- **Nevytvářej repos mimo org** — všechno žije v codetogodmode

## Když se zasekneš

1. `git status` — ukaž si co se děje
2. `git log --oneline -10` — ukaž si posledních 10 commitů
3. `git diff` — ukaž si co jsi změnil
4. Pokud je to fakt špatně — **NEPANIKAŘ**. Napiš do #help, vyřešíme to.

## Užitečné příkazy

```bash
git status              # co se děje
git log --oneline -10   # posledních 10 commitů
git diff                # co jsem změnil (unstaged)
git diff --staged       # co jsem přidal do stage
git checkout -b nazev   # nový branch
git add soubor.cs       # přidej soubor do stage
git commit -m "popis"   # commitni
git push                # pošli na GitHub
git pull                # stáhni novinky z GitHubu
git checkout main       # přepni se na main
```

## Proof of Concept / Experimenty

Chceš si něco vyzkoušet? Vytvoř si sandbox repo přes `/new-repo` v #repos na Discordu -- nemusíš čekat na Martina. Klidně to může být `sandbox-tereza-pokus-s-api` nebo `sandbox-petr-kalkulacka-v2`.

Pro strukturovanou práci (session úkoly, gate challenges) používej svůj member repo (`member-{jméno}`). Pro volné experimenty a PoC si vytvoř sandbox. Lepší mít přehledný member repo + pár malých sandboxů než jeden obrovský repo s chaosem.
