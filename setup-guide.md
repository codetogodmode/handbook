# Setup Guide

## Krok 1: Prerekvizity

Jdi na [codetogodmode.com](https://codetogodmode.com) a projdi si checklist. Budeš potřebovat přístupový kód od Martina.

Nainstaluj:
1. Discord
2. GitHub účet
3. Visual Studio Code
4. C# Dev Kit (rozšíření do VS Code)
5. .NET 10 SDK
6. Git

## Krok 2: Připoj se do týmu

Po instalaci napiš Martinovi své **GitHub uživatelské jméno** (to z URL: github.com/tvoje-jmeno). Martin tě přidá do organizace [codetogodmode](https://github.com/codetogodmode).

## Krok 3: Ověř prostředí

Otevři terminál ve VS Code — to je textové okno, kde píšeš příkazy místo klikání:
- **Klávesnice:** `Ctrl+středník` (na české klávesnici) nebo `Ctrl+backtick` (na anglické)
- **Přes menu:** nahoře klikni na **Terminal → New Terminal**

Ověř:

```bash
dotnet --version
# Mělo by zobrazit 10.0.xxx

git --version
# Mělo by zobrazit číslo verze
```

## VS Code — jak spouštět a debugovat

### Theme
Doporučujeme **Dark Modern** — přepneš přes `Ctrl+K` a pak `Ctrl+T`, nebo nahoře **File → Preferences → Color Theme**.

### Spuštění programu
Máš dvě možnosti:
- **Tlačítko ▶ vpravo nahoře** v editoru → vyber **Run** — nejrychlejší způsob
- **V terminálu:** `dotnet run --project src/NazevProjektu`

### Debug (hledání chyb)
Debug ti umožní zastavit program na libovolném řádku a podívat se na hodnoty proměnných:

1. **Nastav breakpoint** — klikni na číslo řádku vlevo od kódu. Objeví se červená tečka.
2. **Spusť v debug režimu** — klikni na ▶ vpravo nahoře → vyber **Debug** (ne Run). Nebo stiskni **F5**.
3. **Program se zastaví** na breakpointu. Vlevo uvidíš panel s hodnotami proměnných.
4. **Krokování:**
   - **F10** — další řádek (přeskočí dovnitř metody)
   - **F11** — vstup do metody
   - **F5** — pokračuj až do dalšího breakpointu
5. **Watch** — v debug panelu vlevo můžeš přidat výrazy, které chceš sledovat

Debug se naučíš na sessions — tady je to jen pro přehled.

## Krok 4: Přečti si pravidla

- [Pravidla](pravidla.md) -- jak fungujeme
- [AI Policy](ai-policy.md) -- jak smíš/nesmíš používat AI
- [AI Tools Guide](ai-tools-guide.md) -- průvodce AI nástroji pro každý režim
- [GitHub Guide](github-guide.md) -- jak pracujeme s GitHubem
- [Secrets Guide](secrets-guide.md) -- jak zacházet s hesly, klíči a tokeny
- [Definition of Done](definition-of-done.md) -- kdy je úkol hotový
- [Roadmap](roadmap.md) -- co nás čeká

## Krok 5: První session (Session 0)

První session je Session 0 — intro bez kódování. Potkáme se na Discordu v Session Room. Martin představí program, projdeme pravidla, seznámíme se a společně ověříme prostředí. Vy se ptáte, kódovat se ještě nebude.

Přijď s hotovými prerekvizitami (kroky 1-4). Na Session 0 společně ověříme, že máš všechno nainstalované a funkční. Pokud se zasekneš na instalaci, nevadí — projdeme to spolu.

První kódování přijde na řadu v Session 1 (Layer 1), kde si naklonuješ svůj repo, napíšeš první program a pushneš první commit na GitHub.

Neboj se ptát. Nikdo tu nezačínal jako expert.
