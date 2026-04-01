# Secrets Guide — Jak zacházet s hesly, klíči a tokeny

## Co jsou secrets

Secrets (tajemství) jsou citlivé údaje, které tvůj program potřebuje, aby se mohl připojit k nějaké službe nebo provést něco, co vyžaduje oprávnění. Patří sem:

- **API key** — klíč, který ti dá nějaká služba (třeba OpenAI, GitHub, Azure), abys ji mohl používat. Je to jako heslo ke konkrétní službě. Kdo ho má, může službu používat na tvůj účet.
- **Token** — podobný jako API key, ale obvykle dočasný. Často ho dostaneš po přihlášení a platí omezenou dobu.
- **Heslo** — to klasické. Heslo do databáze, do SMTP serveru pro posílání emailů, do admin panelu.
- **Connection string** — řetězec, který obsahuje adresu serveru, jméno databáze a většinou i heslo. Vypadá třeba takto: `Server=myserver.database.windows.net;Database=mydb;User Id=admin;Password=SuperTajne123;`

Všechny tyhle údaje mají jedno společné: **pokud je někdo získá, může se tvářit jako ty** — posílat emaily, číst data, mazat tabulky, utrácet peníze.

## Proč secrets NIKDY nepatří do kódu ani do gitu

### Co se stane, když secret commitneš

Představ si, že napíšeš tohle:

```csharp
var key = "TAJNY-KLIC"; // NIKDY takhle!
var client = new HttpClient();
client.DefaultRequestHeaders.Add("Authorization", $"Bearer {apiKey}");
```

Vypadá to nevinně. Funguje to. Ale:

1. **Commitneš to do gitu.** Teď je klíč součástí historie repozitáře.
2. **Pushneš na GitHub.** Teď ho vidí každý, kdo má přístup k repozitáři. A pokud je repo veřejné — celý internet.
3. **Automatizované boty** prohledávají GitHub v reálném čase a hledají přesně tyhle patterny. Během minut po pushnutí někdo tvůj klíč zkusí použít.
4. **Výsledek:** Na tvém účtu naběhnou poplatky, někdo pošle spam přes tvůj email server, nebo smaže tvou databázi.

Tohle není teorie. Stává se to každý den. GitHub sám provozuje Secret Scanning, protože je to tak častý problém.

### "Ale já to můžu smazat z dalšího commitu"

Ne, tohle nefunguje. Git si pamatuje **všechno**. I když soubor smažeš nebo řádek přepíšeš, starý commit s klíčem tam pořád je. Kdokoliv si může projít historii a klíč najít.

Jediné řešení je klíč **okamžitě revokovat** (zneplatnit) a vygenerovat nový. Viz sekce "Co dělat, když secret unikne".

## .gitignore a .env soubory

### .env soubor

Soubor `.env` je jednoduchý textový soubor, kde máš secrets uložené lokálně na svém počítači. Vypadá takhle:

```
OPENAI_API_KEY=TADY-BY-BYL-TAJNY-KLIC
DATABASE_PASSWORD=SuperTajne123
SMTP_HOST=smtp.example.com
```

Tvůj program si tyto hodnoty načte za běhu (z environment variables), místo aby je měl natvrdo v kódu.

### .gitignore soubor

Soubor `.gitignore` říká gitu, které soubory má **ignorovat** — nikdy je nesledovat, nikdy je necommitnout. Jeden řádek = jeden pattern.

```gitignore
# Secrets - NIKDY necommitnout
.env
.env.*
appsettings.Development.json

# Build výstupy
bin/
obj/
```

Když je `.env` v `.gitignore`, git ho prostě nevidí. Neukáže se v `git status`, nepůjde commitnout omylem.

### Jak na to prakticky

1. Na začátku projektu vytvoř `.gitignore` (nebo použij template — `dotnet new gitignore`).
2. Přidej do něj `.env` a další citlivé soubory.
3. Commitni `.gitignore` jako první věc.
4. Teprve potom vytvoř `.env` se svými secrets.

### .env.example

Je dobrá praxe mít v repozitáři soubor `.env.example`, který ukazuje **strukturu** bez skutečných hodnot:

```
OPENAI_API_KEY=sem-vloz-svuj-klic
DATABASE_PASSWORD=
SMTP_HOST=
```

Tenhle soubor commitneš normálně. Kdokoliv si klonuje repo, zkopíruje `.env.example` na `.env` a doplní svoje hodnoty.

## Co dělat, když secret unikne

Tohle se stane. I zkušeným vývojářům. Důležité je reagovat rychle.

### Okamžitě — do 5 minut

1. **Revokuj (zneplatni) klíč.** Jdi na stránku služby (GitHub Settings, Azure Portal, OpenAI dashboard) a klíč smaž / vygeneruj nový.
2. **Nahraď klíč všude**, kde ho používáš — v `.env`, v konfiguraci serveru, atd.

### Potom

3. **Odstraň secret z git historie.** Tohle je komplikované (nástroje jako `git filter-repo`), ale nutné u veřejných repozitářů.
4. **Řekni Martinovi**, že se to stalo. Nikdo tě nebude soudit — důležité je, že jsi to řešil rychle.

### Klíčové pravidlo

**Nikdy nepovažuj uniknutý secret za bezpečný jen proto, že jsi ho smazal z kódu.** Dokud ho nezrevokoješ, může ho někdo použít. Git historie, cached stránky, forky repozitáře — klíč může žít na spoustě míst.

## Secrets a AI

Tohle je novější problém a hodně lidí na něj nemyslí.

### NIKDY nesdílej secrets v promptech

Když píšeš do ChatGPT, Claude, Copilotu nebo jakéhokoliv AI nástroje:

- **Nevkládej API keys, tokeny, hesla, connection stringy.**
- **Nedávej screenshoty**, na kterých jsou secrets vidět.
- **Nekopíruj celé konfigurační soubory** s citlivými údaji.

### Proč

- AI konverzace jsou **logovány**. Provozovatel služby je může vidět, použít pro trénink modelu, nebo mohou uniknout.
- I když služba tvrdí, že data nesdílí — nemáš nad tím kontrolu.
- Stačí jeden screenshot s connection stringem v chatu a tvoje databáze je potenciálně kompromitovaná.

### Jak se ptát AI bezpečně

Nahraď skutečné hodnoty placeholdery:

```
-- Špatně:
Muj connection string Server=prod.database.net;Password=Heslo123; nefunguje, proč?

-- Správně:
Muj connection string nefunguje, format je Server=<adresa>;Password=<heslo>; — co můžu zkontrolovat?
```

AI nepotřebuje tvoje skutečné heslo, aby ti pomohla s problémem.

## GitHub Secrets a environment variables

Když tvůj kód běží v CI/CD pipeline (automatické buildy a deploymenty na GitHubu), potřebuje přístup k secrets. GitHub pro to má bezpečné úložiště.

### Jak to funguje

1. V repozitáři na GitHubu jdeš do **Settings > Secrets and variables > Actions**.
2. Klikneš **New repository secret**.
3. Zadáš jméno (třeba `OPENAI_API_KEY`) a hodnotu (skutečný klíč).
4. V GitHub Actions workflow se na secret odkážeš přes `${{ secrets.OPENAI_API_KEY }}`.

```yaml
# .github/workflows/deploy.yml
env:
  OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}
```

### Důležité vlastnosti

- GitHub secret **nikdy neuvidíš znovu** po uložení — můžeš ho jen přepsat novým.
- V logách se secrets automaticky **maskují** (nahradí se hvězdičkami `***`).
- Secrets se **nepřenáší do forků** — nikdo si nemůže forknout tvůj repo a přečíst tvoje klíče.

## Secrets v .NET projektech

V .NET máme tři vrstvy pro konfiguraci, každá pro jiný účel.

### appsettings.json — veřejná konfigurace

Tohle je soubor, který commitneš normálně. Patří sem věci, které **nejsou tajné**:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information"
    }
  },
  "AllowedHosts": "*",
  "AppSettings": {
    "PageSize": 20,
    "AppName": "MojeAplikace"
  }
}
```

Adresy API, velikosti stránek, feature flags — to všechno sem patří. **Hesla a klíče NE.**

### dotnet user-secrets — lokální vývoj

Pro lokální vývoj má .NET vestavěný nástroj `user-secrets`. Secrets se ukládají mimo projekt, v tvém uživatelském profilu — nikdy se nedostanou do gitu.

```bash
# Inicializace (jednou pro projekt)
dotnet user-secrets init

# Uložení secretu
dotnet user-secrets set "ConnectionStrings:DefaultConnection" "Server=localhost;Database=mydb;User Id=sa;Password=MojeTajneHeslo;"

# Zobrazení všech secrets
dotnet user-secrets list
```

V kódu se ke secrets dostaneš úplně stejně jako k běžné konfiguraci:

```csharp
var connectionString = builder.Configuration.GetConnectionString("DefaultConnection");
```

.NET automaticky spojí `appsettings.json` a user-secrets dohromady. V kódu neřešíš, odkud hodnota pochází.

### Environment variables — produkce

Na produkčním serveru (Azure, Docker, Linux server) se secrets nastavují jako environment variables. Každá platforma to řeší trochu jinak:

- **Azure App Service:** Configuration > Application settings
- **Docker:** `docker run -e "ConnectionStrings__DefaultConnection=..." myapp`
- **GitHub Actions:** Přes `secrets` (viz výše)

V .NET se environment variables automaticky mapují na konfiguraci. Dvojité podtržítko (`__`) nahrazuje dvojtečku (`:`) z JSON struktury:

```bash
# Tohle se v kódu čte jako Configuration["ConnectionStrings:DefaultConnection"]
export ConnectionStrings__DefaultConnection="Server=prod.database.net;..."
```

### Pořadí priority

.NET čte konfiguraci v tomto pořadí (pozdější přepisuje dřívější):

1. `appsettings.json`
2. `appsettings.{Environment}.json`
3. User secrets (jen v Development)
4. Environment variables
5. Command line argumenty

Takže i když máš v `appsettings.json` placeholder, environment variable na produkci ho přepíše skutečnou hodnotou.

## Shrnutí — pravidla, která platí vždy

1. **Secrets nikdy do kódu.** Ani "dočasně". Ani "jen lokálně". Ani do komentáře.
2. **Secrets nikdy do gitu.** Zkontroluj `.gitignore` dřív, než uděláš první commit.
3. **Secrets nikdy do AI chatu.** Žádné klíče v promptech, screenshotech ani paste.
4. **Když secret unikne — okamžitě revokuj.** Mazání z kódu nestačí.
5. **Používej správné nástroje:** `.env` / `dotnet user-secrets` lokálně, environment variables / GitHub Secrets na serveru.

Pokud si nejsi jistý, jestli je něco secret — chovej se k tomu jako k secretu. Lepší být paranoidní než řešit následky.
