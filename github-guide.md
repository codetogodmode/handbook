# Jak pracujeme s GitHubem

Veškerý kód žije v naší GitHub organizaci **codetogodmode**. Tady je všechno, co potřebuješ vědět.

## Kde co žije

Organizace má několik typů repozitářů:

- **shared-*** — společné projekty, na kterých pracujeme všichni (Layer 1-2)
- **capstone-*** — tvůj osobní projekt (od Layer 3 dál)
- **demo-*** — ukázkový kód ze sessions
- **template-*** — startovní šablony, ze kterých se tvoří nové projekty
- **handbook** — pravidla, dokumenty, návody (tohle čteš právě teď)
- **study-book** — učební materiály ze sessions

**Důležité:** Nevytvářej si repos sám. Když potřebuješ nový repo (PoC, experiment, cokoliv), řekni Martinovi — vytvoří ho z template v organizaci. Tím máš rovnou CI, .gitignore, PR template a správná nastavení.

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
- **Neigonruj review** — pokud nesouhlasíš s komentářem, diskutuj, neignoruj
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

Chceš si něco vyzkoušet mimo hlavní projekt? Řekni Martinovi — vytvoří ti repo z template. Klidně to může být `capstone-tereza-poc-enneagram-parser` nebo `capstone-petr-experiment-api`. Lepší mít 5 malých repů než jeden obrovský s chaosem.
