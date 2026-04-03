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

- Typy, proměnné, enum, podmínky, cykly
- Metody, kolekce, stringy
- Git: clone, commit, push (branching se učí v Layer 2)
- Debugging: breakpointy, watch, stack trace
- **Výstup:** Funkční konzolová appka pushnutá na GitHub
- **AI režim:** EXPLAIN

## Layer 2 — OOP & Quality (~6 sessions, týdny 5-7)

Třídy, testy, refactoring. OOP jako řešení bolesti, ne jako teorie.

- Třídy, objekty, interface, composition
- Git: branching, PR, code review (na shared projektu)
- Unit testy (xUnit)
- Refactoring — "kód smrdí, opravíme ho"
- **Výstup:** Domain model s testy, sdílený projekt s PR workflow
- **AI režim:** EXPLAIN → drilling na HELPER

## Layer 3 — Data & API (~7 sessions, týdny 8-10)

Backend, databáze, architektura. Capstone projekty se rozjíždí.

- EF Core, SQLite, LINQ, generics
- async/await
- HTTP, REST, ASP.NET Core (controller-based API)
- Dependency Injection, separation of concerns
- **Výstup:** Backend API s databází — capstone projekty startují
- **AI režim:** HELPER → drilling na PAIR

## Layer 4 — Frontend & Full Stack (~8 sessions, týdny 11-14)

UI pro tvou appku.

- React + Vite + TypeScript + Tailwind CSS
- Komponenty, props, state, formuláře
- Fetch dat z API, CRUD UI
- **Výstup:** Fungující full-stack appka
- **AI režim:** PAIR → drilling na BUILDER
- **Tempo:** Delší rozestupy mezi sessions — frontend je nová doména, procvičení mezi sessions je klíčové

## Layer 5 — Ship It (~4 sessions, týdny 15-16)

Tvoje appka živá na internetu.

- Docker, docker-compose
- PostgreSQL (přechod ze SQLite — jeden řádek konfigurace!)
- CI/CD: GitHub Actions → deploy
- Deployment na Fly.io
- **Výstup:** Appka na vlastní URL
- **AI režim:** BUILDER → drilling na GOD MODE

## AI dovednosti

AI se učíte průběžně v kontextu práce — ne na separátních "AI sessions". Jak postupujete layers, přirozeně narážíte na situace, kde AI pomáhá, a učíte se ho používat správně.

Jediná výjimka: po složení Gate 4 (GOD MODE) proběhne dedikovaná session, kde vás Martin provede svým AI workflow s reálnými nástroji.

## Tempo

- 2 sessions/týden, 1-3 hodiny
- Individuální tempo na projektech
- Gates se odemykají per-member, ne podle kalendáře
