# Roadmap

## Přehled

```
Session 0        Layer 1          Layer 2          Layer 3          Layer 4          Layer 5
Intro            Console & Git    OOP & Quality    Data & API       Frontend         Ship It
(1 session)      (~4 týdny)       (~3 týdny)       (~4 týdny)       (~4 týdny)       (~2 týdny)
    |                |                |                |                |                |
    v                v                v                v                v                v
  (intro)           EXPLAIN -------> HELPER -------> PAIR ----------> BUILDER ------> GOD MODE
```

Celkem: ~17 týdnů + 1 intro session (~4.5 měsíce) při 2 sessions/týden.

## Session 0 — Intro (před Layer 1)

Úvodní session bez kódování. Cílem je, aby se všichni seznámili s programem, s Martinem a navzájem.

- Představení CTGM — co vás čeká, jak program funguje, co je cílem
- Seznámení s členy — co vás zajímá, proč jste tu, co chcete umět
- Přehled pravidel, AI policy, Definition of Done
- Kontrola prerekvizit — společná verifikace, že všichni mají nainstalováno
- **Výstup:** Všichni mají funkční prostředí, přístup do organizace, jasnou představu o programu
- **AI režim:** Žádný — intro session bez AI nástrojů

## Layer 1 — Console & Git (~7 sessions, týdny 1-4)

C# základy, Git od prvního dne, debugging.

| Co se naučíš | Detaily |
|-------------|---------|
| Terminál | `cd`, `ls`, `mkdir` — orientace v příkazové řádce |
| Hello World | Program.cs, `dotnet run` — první program |
| Proměnné a typy | `int`, `string`, `bool`, `double` — jak data vypadají |
| Enum | Pojmenované konstanty — místo magic numbers |
| Console I/O | `ReadLine`, `WriteLine` — vstup a výstup |
| Podmínky | `if/else`, `switch` — program se rozhoduje |
| Cykly | `for`, `while`, `foreach` — opakování |
| Metody | Parametry, návratové hodnoty — rozděl kód na kousky |
| Kolekce | `List<T>`, `Dictionary<K,V>` — pracuj se skupinou dat |
| String operace | Interpolace, formátování — text v programu |
| Git | clone, add, commit, push, status, log, diff |
| Debugging | Breakpointy, watch, stack trace — najdi co je špatně |

- **Výstup:** Funkční konzolová appka pushnutá na GitHub
- **AI režim:** EXPLAIN

## Layer 2 — OOP & Quality (~6 sessions, týdny 5-7)

Třídy, testy, refactoring. OOP jako řešení bolesti, ne jako teorie.

| Co se naučíš | Detaily |
|-------------|---------|
| Třídy a objekty | Fields, konstruktor, metody — organizuj kód smysluplně |
| Properties | Get/set, auto-properties — kontrolovaný přístup k datům |
| Encapsulation | Private/public — schovej co nemá být vidět |
| Composition | Objekt obsahuje objekty — skládej stavební bloky |
| Interface | Kontrakty — "slibuju že umím toto" |
| Git: branching | Branch, checkout, merge — pracuj na vlastní kopii |
| Git: PR + review | Pull Request — code review od kolegů |
| Unit testing | xUnit, Arrange/Act/Assert — ověř že kód dělá co má |
| Code smells | Duplikace, god class — poznáš když kód smrdí |
| Refactoring | Extract method/class — oprav co smrdí |
| Separation of concerns | UI vs logika — každá část dělá jednu věc |

- **Výstup:** Domain model s testy, sdílený projekt s PR workflow
- **AI režim:** EXPLAIN → drilling na HELPER

## Layer 3 — Data & API (~7 sessions, týdny 8-10)

Backend, databáze, architektura. Capstone projekty se rozjíždí.

| Co se naučíš | Detaily |
|-------------|---------|
| SQL základy | SELECT, INSERT, WHERE — jak databáze funguje |
| EF Core + SQLite | DbContext, entity, migrace — C# mluví s databází |
| Generics | `<T>` — piš kód který funguje s jakýmkoliv typem |
| Lambda výrazy | `=>` syntax — zkrácený zápis pro metody |
| LINQ | Where, Select, OrderBy — dotazy nad kolekcemi |
| async/await | Task, async metody — neblokuj program |
| HTTP | Verby, status kódy, JSON — jak web komunikuje |
| Controller API | ASP.NET Core — tvůj backend odpovídá na requesty |
| REST | Resource URLs, CRUD — konvence pro API design |
| Service layer | Interface + implementace — čistá architektura |
| Dependency Injection | Registrace, constructor injection — flexibilní propojení |

- **Výstup:** Backend API s databází — capstone projekty startují
- **AI režim:** HELPER → drilling na PAIR

## Layer 4 — Frontend & Full Stack (~8 sessions, týdny 11-14)

UI pro tvou appku.

| Co se naučíš | Detaily |
|-------------|---------|
| HTML/CSS | Základy webových stránek — struktura a styling |
| TypeScript | Typovaný JavaScript — syntaxí podobný C# |
| React + Vite | Komponenty, JSX — moderní frontend framework |
| Props a State | Předávání dat, `useState` — dynamické UI |
| useEffect | Lifecycle, side effects — načítání dat |
| Fetch z API | Napojení na tvůj backend — reálná data v UI |
| Formuláře | Controlled components — uživatel zadává data |
| CRUD UI | Create, edit, delete — kompletní operace v prohlížeči |
| Routing | React Router — více stránek v jedné appce |
| Tailwind CSS | Utility-first styling — rychlý a konzistentní design |

- **Výstup:** Fungující full-stack appka
- **AI režim:** PAIR → drilling na BUILDER
- **Tempo:** Delší rozestupy mezi sessions — frontend je nová doména, procvičení mezi sessions je klíčové

## Layer 5 — Ship It (~4 sessions, týdny 15-16)

Tvoje appka živá na internetu.

| Co se naučíš | Detaily |
|-------------|---------|
| Docker | Image, container, Dockerfile — zabal appku |
| docker-compose | Multi-container setup — API + DB + frontend spolu |
| PostgreSQL | Přechod ze SQLite — jeden řádek konfigurace! |
| Environment variables | Secrets management — bezpečná konfigurace |
| GitHub Actions | CI/CD pipeline — automatický build a test |
| Deployment | Fly.io — tvoje appka na vlastní URL |

- **Výstup:** Appka na vlastní URL
- **AI režim:** BUILDER → drilling na GOD MODE

## AI dovednosti

AI se učíte průběžně v kontextu práce — ne na separátních "AI sessions". Jak postupujete layers, přirozeně narážíte na situace, kde AI pomáhá, a učíte se ho používat správně.

Jediná výjimka: po složení Gate 4 (GOD MODE) proběhne dedikovaná session, kde vás Martin provede svým AI workflow s reálnými nástroji.

## Tempo

- 2 sessions/týden, 1-3 hodiny
- Individuální tempo na projektech
- Gates se odemykají per-member, ne podle kalendáře
