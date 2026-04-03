# AI Policy

## Filosofie

AI je motor — ale někdo musí vědět kam jet a kdy zabrzdit. Naučíme tě řídit, než ti dáme turbo.

## 5 režimů

Každý režim se odemyká individuálně na základě toho, co umíš — ne podle toho, kolik týdnů uběhlo.

### Režim 0 — EXPLAIN

> Dostupný od prvního dne.

**Smíš:** Ptát se AI na vysvětlení konceptů, chybových hlášek, stack trace. Nechat si vysvětlit kód. Rubber ducking.

**Nesmíš:** Nechat AI generovat kód za tebe.

### Režim 1 — HELPER

**Smíš:** Požádat AI o nápady na refactoring, test cases, pojmenování, boilerplate, regex, README.

**Nesmíš:** Nechat AI implementovat celý úkol.

**Gate:** Umíš přečíst stack trace, opravit bug debuggerem, vysvětlit co jsi udělal.

### Režim 2 — PAIR

**Smíš:** Spolupracovat s AI na malém ticketu. Vždy přes issue → branch → PR → review. S AI disclosure v PR.

**Nesmíš:** Pushovat bez review.

**Gate:** Umíš napsat třídu, napsat test, vysvětlit call flow.

### Režim 3 — BUILDER

**Smíš:** Nechat AI implementovat větší features. Architekturní návrhy. Paralelní práce.

**Nesmíš:** Pushovat rovnou na main. Pracovat bez testů.

**Gate:** Umíš postavit API endpoint, použít DI, vysvětlit architekturu.

### Režim 4 — GOD MODE

**Smíš:** Plný vibe coding — Claude Code, Codex, agentické workflow. Všechno.

**Nesmíš:** Nic bez zodpovědnosti. Vždy review. Vždy rollback path. Vždy rozumíš tomu, co se děje.

**Gate:** Umíš reviewovat AI diff, rollbacknout změnu, identifikovat rizika.

## Jak se odemykají gates

Martin ti zadá challenge — buď jako kód s bugem k opravení (nižší gates), nebo jako live 1:1 drilling session (vyšší gates). Nejde o test — jde o ověření, že jsi ready na další úroveň.

Nemusíš to teď umět. Každou dovednost z gate kritérií se nejdřív naučíš na sessions — gate jen ověří, že to sedí.

## AI disclosure v pull requestech

Každý PR, kde AI pomáhala, musí obsahovat:

1. **Co bylo zadání** — co jsi chtěl udělat
2. **Co AI navrhla** — co ti AI vygenerovala
3. **Co jsi nechal / zahodil** — tvoje rozhodnutí
4. **Jak jsi to ověřil** — jak víš, že to funguje

## Zlaté pravidlo

**Nikdy neodevzdáš kód, kterému nerozumíš. Ani v God Mode.**
