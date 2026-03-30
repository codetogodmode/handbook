# AI Tools Guide

Průvodce AI nástroji pro každý režim. Nemusíš si všechno nastavovat hned — vždy si přečti jen sekci pro svůj aktuální režim.

## Přehled

| Režim | Nástroj | Setup |
|-------|---------|-------|
| EXPLAIN | Discord bot (`!ask`) | Nic — už to máš |
| HELPER | ChatGPT / Claude (prohlížeč) | Založit free účet, vložit system prompt |
| PAIR | ChatGPT / Claude (prohlížeč) | Stejný účet, jiný system prompt |
| BUILDER | Claude Code (CLI/IDE) | Instalace CLI, CLAUDE.md v projektu |
| GOD MODE | Claude Code / Codex | Plný přístup, vlastní zodpovědnost |

---

## EXPLAIN — Discord bot

**Nástroj:** Bot J.A.R.V.I.S v kanálu #help na našem Discord serveru.

**Jak ho použít:**
Napiš `!ask` a za to svou otázku. Příklady:
- `!ask Co je to proměnná?`
- `!ask Jak funguje foreach cyklus?`
- `!ask Co znamená chyba NullReferenceException?`
- `!ask Jaký je rozdíl mezi int a string?`

**Co bot umí:**
- Vysvětlit koncepty z C# a .NET
- Vysvětlit chybové hlášky
- Odpovědět na otázky o pravidlech a kurikulu (zná náš handbook)

**Co bot neumí / nesmíš:**
- Psát za tebe kód
- Řešit za tebe úkoly
- Pokud bot neví, řekne ti, abys se zeptal Martina

**Setup:** Žádný. Stačí mít Discord a být na serveru.

---

## HELPER — ChatGPT / Claude (prohlížeč)

Tohle je první moment, kdy budeš používat AI mimo Discord. Vyber si jednu z platforem (obě mají free tier):

### Jak založit účet

**ChatGPT:**
1. Jdi na [chatgpt.com](https://chatgpt.com)
2. Klikni "Sign up" a zaregistruj se (Google účet nebo email)
3. Free tier stačí

**Claude:**
1. Jdi na [claude.ai](https://claude.ai)
2. Klikni "Sign up" a zaregistruj se (Google účet nebo email)
3. Free tier stačí

### System prompt — vlož ho před první otázkou

Zkopíruj tento text a vlož ho na začátku každé nové konverzace s AI:

```
You are a coding mentor assistant for a beginner learning C# and .NET.
You are in HELPER mode.

ALLOWED:
- Explain concepts, errors, and stack traces
- Suggest refactoring ideas
- Propose test case ideas
- Help with naming (variables, methods, classes)
- Generate boilerplate code (project structure, empty classes)
- Help with regex, LINQ queries, small utilities

NOT ALLOWED:
- Implement entire features or tasks
- Write complete solutions to assignments
- If the user asks you to implement something, suggest an approach and let them write it

Always respond in Czech. Use English for technical terms (commit, branch, PR, class, interface, method, etc.).
Keep answers concise and practical. Include short code examples where helpful.
```

**Kam ho vložit:**
- **ChatGPT:** Settings → Personalization → Custom Instructions → "How would you like ChatGPT to respond?" → vlož sem
- **Claude:** Na začátek první zprávy v konverzaci, nebo vytvoř Project a vlož do Project Instructions

> **⚠️ Bezpečnost:** Nikdy do AI promptu nevkládej API klíče, tokeny, hesla ani connection stringy. Konverzace s AI mohou být logovány. Pokud tvůj kód obsahuje secrets, odstraň je před vložením.

### Příklady — co se ptát a co ne

**Dobrý prompt (HELPER):**
- "Jak bych měl pojmenovat třídu, která spravuje seznam úkolů?"
- "Jaké testy bych měl napsat pro metodu, co validuje email?"
- "Můžeš mi vysvětlit, co dělá tento kód?" + kód
- "Jak refaktorovat tuhle metodu, aby byla kratší?"

**Špatný prompt (porušuje HELPER):**
- "Napiš mi celou kalkulačku v C#"
- "Implementuj CRUD API pro správu uživatelů"
- "Dokonči za mě tento úkol"

Pokud AI nabídne hotový kód, nepřijímej ho celý. Požádej o vysvětlení přístupu a napiš to sám.

---

## PAIR — ChatGPT / Claude (prohlížeč)

Stejný nástroj jako HELPER, ale s rozšířenými pravidly. AI teď smí psát kód — ale ty ho vždy kontroluješ a kopíruješ ručně.

### System prompt pro PAIR

Nahraď HELPER prompt tímhle:

```
You are a coding assistant for a junior C#/.NET developer.
You are in PAIR mode.

ALLOWED:
- Help implement small, well-defined tasks
- Write code snippets and explain what they do
- Suggest architecture for small features
- Help debug issues with code context
- Everything from HELPER mode

NOT ALLOWED:
- Implement large features without breaking them into steps
- Make decisions about project architecture without explaining trade-offs
- Skip explanations — always explain what the code does and why

WORKFLOW REMINDER:
After helping with implementation, remind the user to:
1. Copy the code and adapt it (don't paste blindly)
2. Test it
3. Commit with a meaningful message
4. Open a PR with AI disclosure

Always respond in Czech. Use English for technical terms.
Be specific, provide working code, explain every non-obvious line.
```

> **⚠️ Bezpečnost:** Nikdy do AI promptu nevkládej API klíče, tokeny, hesla ani connection stringy. Konverzace s AI mohou být logovány. Pokud tvůj kód obsahuje secrets, odstraň je před vložením.

### Workflow

1. Máš issue (task v GitHubu)
2. Vytvoříš branch
3. Otevřeš konverzaci s AI, popíšeš úkol
4. AI navrhne řešení — přečti ho, porozuměj, zkopíruj co dává smysl
5. Uprav, otestuj, commitni
6. Otevři PR s AI disclosure (co AI navrhla, co jsi nechal/zahodil, jak jsi to ověřil)

### Příklady — dobrý PAIR prompt

- "Mám třídu `TodoItem` s properties `Title`, `IsCompleted`, `CreatedAt`. Potřebuju metodu `MarkAsCompleted()` — napiš ji a vysvětli co dělá."
- "Tady je můj controller (kód). Potřebuju přidat endpoint pro smazání úkolu podle ID. Ukaž mi jak."

---

## BUILDER — Claude Code

Claude Code je CLI nástroj, který pracuje přímo s tvými soubory. Píše kód do tvého projektu, spouští příkazy, dělá commity. Ty reviewuješ co udělal.

### Instalace

```bash
npm install -g @anthropic-ai/claude-code
```

(Budeš potřebovat Anthropic API klíč nebo Claude Max předplatné — zeptej se Martina)

### CLAUDE.md v projektu

V rootu tvého projektu vytvoř soubor `CLAUDE.md`:

```markdown
# Project Rules

- Never commit automatically — always wait for review
- Before making changes, describe what you plan to do
- Write tests for every new function
- Use Czech language in comments and commit messages
- After completing work, remind about AI disclosure for PR
- Keep code simple — prefer clarity over cleverness
```

Claude Code tento soubor přečte automaticky a bude se řídit pravidly.

> **⚠️ Bezpečnost:** Nikdy do AI promptu nevkládej API klíče, tokeny, hesla ani connection stringy. Konverzace s AI mohou být logovány. Pokud tvůj kód obsahuje secrets, odstraň je před vložením.

### Jak pracovat s Claude Code

1. Otevři terminál v projektu
2. Spusť `claude`
3. Popiš co chceš udělat: "Přidej endpoint pro smazání úkolu podle ID"
4. Claude Code navrhne změny — **projdi si diff** (co přesně změnil)
5. Pokud souhlasíš, nech ho aplikovat
6. Spusť testy: `dotnet test`
7. Commitni a otevři PR

### Pravidla

- Nikdy neschvaluj změny, kterým nerozumíš
- Vždy si přečti diff před potvrzením
- Pokud Claude Code něco rozbije, `git checkout -- .` vrátí stav zpět

---

## GOD MODE — Plný přístup

Claude Code nebo Codex bez omezení. Agentické workflow — AI pracuje paralelně, generuje celé features, řeší architekturu.

**Žádné guardraily v promptu.** Zodpovědnost je na tobě.

I v God Mode platí:
- Vždy review, vždy testy, vždy rollback path
- Nikdy neodevzdáš kód, kterému nerozumíš
- AI disclosure v každém PR

> **⚠️ Bezpečnost:** Nikdy do AI promptu nevkládej API klíče, tokeny, hesla ani connection stringy. Konverzace s AI mohou být logovány. Pokud tvůj kód obsahuje secrets, odstraň je před vložením.
