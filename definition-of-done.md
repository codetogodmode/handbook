# Definition of Done

Úkol je hotový, když splňuje **všechny** body:

1. **Kód běží** — bez chyb, dělá to co má
2. **Build projde** — CI (automatická kontrola na GitHubu) je zelený
3. **Testy projdou** — nebo existuje jasný acceptance checklist
4. **Autor umí vysvětlit tok kódu** — od vstupu po výstup, co se kde děje
5. **AI disclosure** — pokud AI pomáhala, je to přiznané
6. **Žádné secrets v kódu** — žádné API klíče, tokeny ani hesla natvrdo v kódu. Použij `.gitignore` a environment variables.

### Od Layer 2 navíc:

7. **PR je otevřený** — s popisem co se změnilo a proč
8. **Code review proběhl** — schválení od Martina nebo peer review

> V Layer 1 se pushuje rovnou na main a PR workflow se ještě nepoužívá. Body 7-8 platí od chvíle, kdy začneš pracovat s branchemi a pull requesty (Layer 2 a dál).

## Proč to děláme

"Funguje to u mě na počítači" není definice hotova. Tenhle checklist existuje proto, abys si zvykl na kvalitu, která se čeká v reálném sw týmu.
