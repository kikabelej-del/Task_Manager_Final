# Testovací případy – Správce úkolů (Task Manager)
Tento dokument obsahuje kompletní sadu testovacích případů (TC) pro ověření funkčnosti aplikace podle stanoveného zadání.

---

## 1. Funkce: hlavni_menu (Navigace a validace volby)

---

### TC01: Spuštění programu a zobrazení hlavního menu

**Název testovacího případu:** Spuštění programu a zobrazení hlavního menu

**Popis:** Ověření, že po spuštění programu se zobrazí hlavní menu s nabídkou voleb 1–4.

**Vstupní podmínky:** Program není spuštěn.

**Kroky testu:**

1. Spusťte program.
   
3. Stisknete Enter.
   
**Očekávaný výsledek:** Program zobrazí hlavní menu s nabídkou voleb „1. Přidat nový úkol", „2. Zobrazit všechny úkoly", „3. Odstranit úkol", „4. Konec programu".

**Skutečný výsledek:** Program se po spuštění správně zobrazil s hlavním menu obsahujícím nabídku voleb „1. Přidat nový úkol", „2. Zobrazit všechny úkoly", „3. Odstranit úkol" a „4. Konec programu".

**Stav:** Pass 

**Poznámky:** Základní smoke test ověřující spuštění programu.

---

### TC02: Výběr platné možnosti 1 z menu

**Název testovacího případu:** Výběr platné možnosti 1 z menu

**Popis:** Ověření, že zadání volby „1" v hlavním menu správně spustí funkci pridat_ukol a vyzve uživatele k zadání názvu úkolu.

**Vstupní podmínky:** Program zobrazuje hlavní menu.

**Kroky testu:**

1. Spusťte program.

2. Ověřte, že se zobrazuje hlavní menu s nabídkou voleb (1–4).

3. Zadejte číslo `1` a potvrďte klávesou Enter.

**Očekávaný výsledek:** Program spustí funkci pridat_ukol() a vyzve uživatele k zadání názvu úkolu (např. „Zadejte název úkolu:").

**Skutečný výsledek:** Po zadání volby „1" program správně přešel do funkce pridat_ukol() a zobrazil výzvu „Zadejte název úkolu:".

**Stav:** Pass 

**Poznámky:** Ověřuje základní navigaci z hlavního menu do funkce pridat_ukol.

---

### TC03: Zadání neplatného vstupu „ABC" v hlavním menu

**Název testovacího případu:** Zadání textu místo čísla volby

**Popis:** Ověření, že program nespadne, pokud uživatel zadá neplatný znak „ABC" namísto platné volby, a znovu zobrazí menu.

**Vstupní podmínky:** Program zobrazuje hlavní menu.

**Kroky testu:**

1. Spusťte program.

2. Do výzvy pro výběr volby zadejte `ABC`.

3. Potvrďte klávesou Enter.

**Očekávaný výsledek:** Program zobrazí chybové hlášení „Neplatná volba, zkuste to znovu (zadejte 1-4).", nespadne a znovu vypíše hlavní menu.

**Skutečný výsledek:** Program nezhavaroval, zobrazil chybové hlášení „Neplatná volba, zkuste to znovu (zadejte 1-4)." a znovu vypsal hlavní menu.

**Stav:** Pass

**Poznámky:** Test robustnosti proti nesprávnému typu dat – nečíselný vstup.

---

### TC04: Zadání neplatné volby „0" v hlavním menu

**Název testovacího případu:** Zadání čísla 0 mimo platný rozsah

**Popis:** Ověření, že zadání hodnoty „0" namísto platné volby zobrazí chybové hlášení.

**Vstupní podmínky:** Program zobrazuje hlavní menu.

**Kroky testu:**

1. Spusťte program.

2. Zadejte `0` a potvrďte klávesou Enter.

**Očekávaný výsledek:** Program zobrazí chybové hlášení „Neplatná volba, zkuste to znovu (zadejte 1-4)." a znovu zobrazí hlavní menu.

**Skutečný výsledek:** Program zobrazil chybové hlášení „Neplatná volba, zkuste to znovu (zadejte 1-4)." a znovu zobrazil hlavní menu bez pádu aplikace.

**Stav:** Pass 

**Poznámky:** Hraniční hodnota – číslo těsně pod platným rozsahem.

---

### TC05: Zadání neplatné volby „5" v hlavním menu

**Název testovacího případu:** Zadání čísla 5 mimo platný rozsah

**Popis:** Ověření, že zadání hodnoty „5" namísto platné volby zobrazí chybové hlášení.

**Vstupní podmínky:** Program zobrazuje hlavní menu.

**Kroky testu:**

1. Spusťte program.

2. Zadejte `5` a potvrďte klávesou Enter.

**Očekávaný výsledek:** Program zobrazí chybové hlášení „Neplatná volba, zkuste to znovu (zadejte 1-4)." a znovu zobrazí hlavní menu.

**Skutečný výsledek:** Program zobrazil chybové hlášení „Neplatná volba, zkuste to znovu (zadejte 1-4)." a znovu zobrazil hlavní menu bez pádu aplikace.

**Stav:** Pass 

**Poznámky:** Hraniční hodnota – číslo těsně nad platným rozsahem.

---

### TC06: Zadání neplatné volby „-1" v hlavním menu

**Název testovacího případu:** Zadání záporného čísla v hlavním menu

**Popis:** Ověření, že zadání záporné hodnoty „-1" namísto platné volby zobrazí chybové hlášení.

**Vstupní podmínky:** Program zobrazuje hlavní menu.

**Kroky testu:**

1. Spusťte program.

2. Zadejte `-1` a potvrďte klávesou Enter.

**Očekávaný výsledek:** Program zobrazí chybové hlášení „Neplatná volba, zkuste to znovu (zadejte 1-4)." a znovu zobrazí hlavní menu.

**Skutečný výsledek:** Program zobrazil chybové hlášení „Neplatná volba, zkuste to znovu (zadejte 1-4)." a znovu zobrazil hlavní menu bez pádu aplikace.

**Stav:** Pass 

**Poznámky:** Negativní vstup – záporné číslo mimo platný rozsah.

---

## 2. Funkce: pridat_ukol (Vytváření úkolů)

---

### TC07: Zadání platného názvu úkolu „červená"

**Název testovacího případu:** Zadání platného názvu úkolu

**Popis:** Ověření, že po zadání platného názvu úkolu program vyzve uživatele k zadání popisu.

**Vstupní podmínky:** Program je spuštěn, uživatel zvolil volbu 1.

**Kroky testu:**

1. Spusťte program.

2. Zadejte volbu `1` a potvrďte klávesou Enter.

3. Na výzvu „Zadejte název úkolu:" zadejte `červená` a potvrďte klávesou Enter.

**Očekávaný výsledek:** Program vyzve uživatele k zadání popisu úkolu (např. „Zadejte popis úkolu:").

**Skutečný výsledek:** Po zadání názvu „červená" program vyzval uživatele k zadání popisu úkolu výzvou „Zadejte popis úkolu:".

**Stav:** Pass 

**Poznámky:** Ověřuje základní pozitivní průchod funkcí pridat_ukol.

---

### TC08: Zadání platného popisu úkolu „modrá" a uložení

**Název testovacího případu:** Úspěšné přidání úkolu s názvem a popisem

**Popis:** Ověření, že po zadání platného názvu i popisu je úkol úspěšně přidán do seznamu.

**Vstupní podmínky:** Program je spuštěn, uživatel zvolil volbu 1 a zadal název „červená".

**Kroky testu:**

1. Spusťte program.

2. Zadejte volbu `1`.

3. Na výzvu „Zadejte název úkolu:" zadejte `červená` a potvrďte klávesou Enter.

4. Na výzvu „Zadejte popis úkolu:" zadejte `modrá` a potvrďte klávesou Enter.

**Očekávaný výsledek:** Program zobrazí potvrzení „Úkol 'červená' byl úspěšně přidán." a vrátí uživatele do hlavního menu.

**Skutečný výsledek:** Po zadání názvu „červená" a popisu „modrá" program zobrazil potvrzení „Úkol 'červená' byl úspěšně přidán." a vrátil uživatele do hlavního menu.

**Stav:** Pass 

**Poznámky:** Kompletní pozitivní průchod přidáním úkolu.

---

### TC09: Zadání dlouhého alfanumerického řetězce jako název úkolu

**Název testovacího případu:** Podpora dlouhého alfanumerického vstupu v názvu

**Popis:** Ověření, že program správně přijme a uloží dlouhý alfanumerický řetězec jako název úkolu.

**Vstupní podmínky:** Program je spuštěn, uživatel zvolil volbu 1.

**Kroky testu:**

1. Spusťte program.

2. Zadejte volbu `1`.

3. Jako název zadejte `ASDFGHJKLYXCVBNMQWERTZUIOP123456789` a potvrďte klávesou Enter.

4. Zadejte libovolný platný popis a potvrďte klávesou Enter.

**Očekávaný výsledek:** Úkol je úspěšně uložen a program zobrazí potvrzující hlášení.

**Skutečný výsledek:** Program přijal dlouhý alfanumerický řetězec jako název úkolu, úkol uložil a zobrazil potvrzující hlášení.

**Stav:** Pass 

**Poznámky:** Ověřuje chování při dlouhém alfanumerickém vstupu v názvu.

---

### TC10: Zadání dlouhého alfanumerického řetězce jako popis úkolu

**Název testovacího případu:** Podpora dlouhého alfanumerického vstupu v popisu

**Popis:** Ověření, že program správně přijme a uloží dlouhý alfanumerický řetězec jako popis úkolu.

**Vstupní podmínky:** Program je spuštěn, uživatel zvolil volbu 1.

**Kroky testu:**

1. Spusťte program.

2. Zadejte volbu `1`.

3. Zadejte libovolný platný název a potvrďte klávesou Enter.

4. Jako popis zadejte `ASDFGHJKLYXCVBNMQWERTZUIOP123456789` a potvrďte klávesou Enter.

**Očekávaný výsledek:** Úkol je úspěšně uložen a program zobrazí potvrzující hlášení.

**Skutečný výsledek:** Program přijal dlouhý alfanumerický řetězec jako popis úkolu, úkol uložil a zobrazil potvrzující hlášení.

**Stav:** Pass 

**Poznámky:** Ověřuje chování při dlouhém alfanumerickém vstupu v popisu.

---

### TC11: Zadání speciálních znaků jako název úkolu

**Název testovacího případu:** Podpora speciálních znaků ve vstupu názvu

**Popis:** Ověření, že program přijme a správně uloží speciální znaky `(/)!"_:?` jako název úkolu.

**Vstupní podmínky:** Program je spuštěn, uživatel zvolil volbu 1.

**Kroky testu:**

1. Spusťte program.

2. Zadejte volbu `1`.

3. Jako název zadejte `(/)!"_:?` a potvrďte klávesou Enter.

4. Zadejte libovolný platný popis a potvrďte klávesou Enter.

**Očekávaný výsledek:** Úkol je úspěšně uložen bez chyb kódování a program zobrazí potvrzující hlášení.

**Skutečný výsledek:** Program přijal speciální znaky (/)!"_:? jako název úkolu bez chyb kódování, úkol uložil a zobrazil potvrzující hlášení.

**Stav:** Pass 

**Poznámky:** Test znakové sady – speciální znaky v názvu.

---

### TC12: Zadání speciálních znaků jako popis úkolu

**Název testovacího případu:** Podpora speciálních znaků ve vstupu popisu

**Popis:** Ověření, že program přijme a správně uloží speciální znaky `(/)!"_:?` jako popis úkolu

**Vstupní podmínky:** Program je spuštěn, uživatel zvolil volbu 1.

**Kroky testu:**

1. Spusťte program.

2. Zadejte volbu `1`.

3. Zadejte libovolný platný název a potvrďte klávesou Enter.

4. Jako popis zadejte `(/)!"_:?` a potvrďte klávesou Enter.

**Očekávaný výsledek:** Úkol je úspěšně uložen bez chyb kódování a program zobrazí potvrzující hlášení.

**Skutečný výsledek:** Program přijal speciální znaky (/)!"_:? jako popis úkolu bez chyb kódování, úkol uložil a zobrazil potvrzující hlášení.

**Stav:** Pass 

**Poznámky:** Test znakové sady – speciální znaky v popisu.

---

### TC13: Pokus o zadání prázdného názvu úkolu

**Název testovacího případu:** Validace prázdného vstupu u názvu úkolu

**Popis:** Ověření, že program nepovolí vytvořit úkol bez názvu a opakuje výzvu k zadání.

**Vstupní podmínky:** Program je spuštěn, uživatel zvolil volbu 1.

**Kroky testu:**

1. Spusťte program.

2. Zadejte volbu `1`.

3. Do výzvy „Zadejte název úkolu:" nezadávejte nic a stiskněte pouze klávesu Enter.

**Očekávaný výsledek:** Program zobrazí hlášení „Název nesmí bžt prázdný, zkuste to znovu." a znovu vyzve uživatele k zadání názvu úkolu.

**Skutečný výsledek:** Program odmítl prázdný název, zobrazil hlášení „Název nesmí bžt prázdný, zkuste to znovu." a znovu vyzval uživatele k zadání názvu úkolu.

**Stav:** Pass 

**Poznámky:** Negativní test na povinné pole – prázdný název nesmí být akceptován.

---

### TC14: Pokus o zadání prázdného popisu úkolu

**Název testovacího případu:** Validace prázdného vstupu u popisu úkolu

**Popis:** Ověření, že program nepovolí vytvořit úkol bez popisu a opakuje výzvu k zadání.

**Vstupní podmínky:** Program je spuštěn, uživatel zvolil volbu 1 a zadal platný název.

**Kroky testu:**

1. Spusťte program.

2. Zadejte volbu `1`.

3. Zadejte platný název a potvrďte klávesou Enter.

4. Do výzvy „Zadejte popis úkolu:" nezadávejte nic a stiskněte pouze klávesu Enter.

**Očekávaný výsledek:** Program zobrazí hlášení „Popis nesmí být prázdný, zkuste to znovu." a znovu vyzve uživatele k zadání popisu úkolu.

**Skutečný výsledek:** Program odmítl prázdný popis, zobrazil hlášení „Popis nesmí být prázdný, zkuste to znovu." a znovu vyzval uživatele k zadání popisu úkolu.

**Stav:** Pass 

**Poznámky:** Negativní test na povinné pole – prázdný popis nesmí být akceptován.

---

### TC15: Přidání duplicitního úkolu (stejný název i popis)

**Název testovacího případu:** Vytvoření úkolu se stejným názvem i popisem

**Popis:** Ověření, jak se systém chová při zadání úkolu, který již v seznamu existuje se stejným názvem i popisem.

**Vstupní podmínky:** V seznamu již existuje úkol s názvem „červená" a popisem „modrá".

**Kroky testu:**

1. Spusťte program.

2. Zadejte volbu `1`, zadejte název `červená` a popis `modrá`.


3. Zadejte znovu volbu `1`, zadejte název `červená` a popis `modrá`.

**Očekávaný výsledek:** Program úkol přidá jako novou položku pod novým pořadovým číslem a zobrazí potvrzující hlášení.

**Skutečný výsledek:** Program přidal druhý úkol se stejným názvem i popisem jako novou položku s novým pořadovým číslem a zobrazil potvrzující hlášení.

**Stav:** Pass 

**Poznámky:** Ověření logiky duplicitních dat – systém neblokuje duplicitní záznamy.

---

## 3. Funkce: zobrazit_ukoly (Výpis dat)

---

### TC16: Zobrazení seznamu s uloženými úkoly

**Název testovacího případu:** Kontrola formátu zobrazení úkolů

**Popis:** Ověření, že se úkoly vypisují s automatickým číslováním od indexu 1 ve formátu „Název - Popis".

**Vstupní podmínky:** V systému je uložen alespoň jeden úkol.

**Kroky testu:**

1. Spusťte program.

2. Přidejte alespoň jeden úkol (volba `1`).

3. V hlavním menu zvolte možnost `2` (Zobrazit všechny úkoly).

**Očekávaný výsledek:** Zobrazí se seznam úkolů, kde každý řádek začíná správným pořadovým číslem (1, 2, ...) následovaným názvem a popisem úkolu.

**Skutečný výsledek:** Program zobrazil seznam úkolů, kde každý řádek byl správně očíslován od indexu 1 ve formátu „číslo. Název - Popis".

**Stav:** Pass 

**Poznámky:** Základní pozitivní test zobrazení.

---

### TC17: Pokus o zobrazení seznamu, pokud je prázdný

**Název testovacího případu:** Kontrola výpisu při nulovém počtu úkolů

**Popis:** Ověření, že program korektně informuje uživatele, pokud v systému nejsou žádná data.

**Vstupní podmínky:** Seznam úkolů je zcela prázdný.

**Kroky testu:**

1. Spusťte program (bez přidání úkolu).

2. V hlavním menu zadejte volbu `2` a potvrďte klávesou Enter.

**Očekávaný výsledek:** Program zobrazí jasný text: „Seznam úkolů je prázdný." a vrátí uživatele do hlavního menu.

**Skutočný výsledek:** Program zobrazil hlášení „Seznam úkolů je prázdný." a vrátil uživatele do hlavního menu.

**Stav:** Pass 

**Poznámky:** Hraniční stav systému – prázdný seznam.

---

### TC18: Ověření přepočítání pořadových čísel po smazání úkolu

**Název testovacího případu:** Kontrola přeindexování zbylých úkolů

**Popis:** Ověření, že po smazání úkolu číslo 1 se původní úkol číslo 2 posune na index 1.

**Vstupní podmínky:** V systému jsou uloženy alespoň dva úkoly (např. 1. Úkol A, 2. Úkol B).

**Kroky testu:**

1. Spusťte program.

2. Přidejte dva úkoly (volba `1`): např. „Úkol A" a „Úkol B".

3. Zadejte volbu `3` a odstraňte úkol číslo `1` (Úkol A).

4. Zadejte volbu `2` a zobrazte seznam.

**Očekávaný výsledek:** V seznamu zůstane pouze jeden úkol (Úkol B) a bude správně očíslován jako číslo 1.

**Skutečný výsledek:** Po smazání úkolu číslo 1 (Úkol A) program zobrazil seznam s jediným zbývajícím úkolem (Úkol B) správně očíslovaným jako číslo 1.

**Stav:** Pass 

**Poznámky:** Test integrity datové struktury – správné přeindexování po smazání položky.

---

## 4. Funkce: odstranit_ukol (Mazání dat a indexace)

---

### TC19: Zobrazení seznamu a výzva při volbě odstranění

**Název testovacího případu:** Spuštění funkce pro odstranění úkolu

**Popis:** Ověření, že volba `3` zobrazí seznam úkolů a vyzve uživatele k zadání čísla úkolu, který má být odstraněn.

**Vstupní podmínky:** Program je spuštěn, v seznamu je alespoň jeden úkol.

**Kroky testu:**

1. Spusťte program.

2. Přidejte alespoň jeden úkol (volba `1`).

3. V hlavním menu zadejte volbu `3`.

**Očekávaný výsledek:** Program zobrazí aktuální seznam úkolů a vyzve uživatele k zadání čísla úkolu, který má být odstraněn.

**Skutečný výsledek:** Po zadání volby „3" program zobrazil aktuální seznam úkolů a vyzval uživatele k zadání čísla úkolu, který má být odstraněn.

**Stav:** Pass 

**Poznámky:** Ověřuje vstupní bod funkce odstranit_ukol.

---

### TC20: Zadání neexistujícího čísla úkolu „5" při odstraňování

**Název testovacího případu:** Pokus o smazání úkolu mimo rozsah indexů

**Popis:** Ověření, že zadání čísla úkolu, který v seznamu neexistuje (hodnota 5), zobrazí chybové hlášení a opakuje výzvu.

**Vstupní podmínky:** Program je spuštěn, v seznamu je méně než 5 úkolů.

**Kroky testu:**

1. Spusťte program.

2. Přidejte méně než 5 úkolů.

3. Zadejte volbu `3`.

4. Jako číslo úkolu ke smazání zadejte hodnotu `5` a potvrďte klávesou Enter.

**Očekávaný výsledek:** Program nesmí spadnout s chybou. Musí zachytit neplatný index, zobrazit hlášení „Neplatná volba, zkuste to znovu." a nechat uživatele zadat číslo znovu.

**Skutečný výsledek:** Program nezhavaroval, zachytil neplatný index, zobrazil hlášení „Neplatná volba, zkuste to znovu." a znovu vyzval uživatele k zadání čísla.

**Stav:** Pass 

**Poznámky:** Negativní test na validaci číselného rozsahu.

---

### TC21: Zadání neplatného vstupu „JKL" namísto čísla při odstraňování

**Název testovacího případu:** Validace datového typu při mazání – nečíselný řetězec

**Popis:** Ověření, že zadání nečíselného řetězce „JKL" namísto čísla úkolu zobrazí chybové hlášení a opakuje výzvu.

**Vstupní podmínky:** Program je spuštěn, v seznamu je alespoň jeden úkol, zobrazena výzva k zadání čísla úkolu.

**Kroky testu:**

1. Spusťte program.

2. Přidejte alespoň jeden úkol.

3. Zadejte volbu `3`.

4. Do výzvy pro číslo úkolu zadejte `JKL` a potvrďte klávesou Enter.

**Očekávaný výsledek:** Program zachytí nesprávný datový typ, nespadne a zobrazí hlášení „Neplatná volba, zkuste to znovu." a znovu vyzve k zadání čísla.

**Skutečný výsledek:** Program zachytil nečíselný vstup, nezhavaroval, zobrazil hlášení „Neplatná volba, zkuste to znovu." a znovu vyzval uživatele k zadání čísla.

**Stav:** Pass 

**Poznámky:** Důležitý test stability kódu – nečíselný vstup při čísle úkolu.

---

### TC22: Zadání názvu úkolu namísto jeho čísla při odstraňování

**Název testovacího případu:** Validace datového typu při mazání – zadání názvu úkolu

**Popis:** Ověření, že zadání názvu úkolu namísto jeho pořadového čísla zobrazí chybové hlášení a opakuje výzvu.

**Vstupní podmínky:** Program je spuštěn, v seznamu je úkol s názvem „červená", zobrazena výzva k zadání čísla úkolu.

**Kroky testu:**

1. Spusťte program.

2. Přidejte úkol s názvem `červená`.

3. Zadejte volbu `3`.

4. Do výzvy pro číslo úkolu zadejte `červená` a potvrďte klávesou Enter.

**Očekávaný výsledek:** Program zachytí nesprávný datový typ, nespadne a zobrazí hlášení „Neplatná volba, zkuste to znovu." a znovu vyzve k zadání čísla.

**Skutečný výsledek:** Program zachytil textový vstup, nezhavaroval, zobrazil hlášení „Neplatná volba, zkuste to znovu." a znovu vyzval uživatele k zadání čísla.

**Stav:** Pass 

**Poznámky:** Negativní test – textový vstup (název) namísto čísla.

---

### TC23: Zadání popisu úkolu namísto jeho čísla při odstraňování

**Název testovacího případu:** Validace datového typu při mazání – zadání popisu úkolu

**Popis:** Ověření, že zadání popisu úkolu namísto jeho pořadového čísla zobrazí chybové hlášení a opakuje výzvu.

**Vstupní podmínky:** Program je spuštěn, v seznamu je úkol s popisem „modrá", zobrazena výzva k zadání čísla úkolu.

**Kroky testu:**

1. Spusťte program.

2. Přidejte úkol s popisem `modrá`.

3. Zadejte volbu `3`.

4. Do výzvy pro číslo úkolu zadejte `modrá` a potvrďte klávesou Enter.

**Očekávaný výsledek:** Program zachytí nesprávný datový typ, nespadne a zobrazí hlášení „Neplatná volba, zkuste to znovu." a znovu vyzve k zadání čísla.

**Skutečný výsledek:** Program zachytil textový vstup, nezhavaroval, zobrazil hlášení „Neplatná volba, zkuste to znovu." a znovu vyzval uživatele k zadání čísla.

**Stav:** Pass

**Poznámky:** Negativní test – textový vstup (popis) namísto čísla.

---

### TC24: Úspěšné odstranění úkolu zadáním platného čísla „1"

**Název testovacího případu:** Odstranění úkolu zadáním platného čísla

**Popis:** Ověření, že zadání platného čísla úkolu způsobí jeho trvalé odstranění ze seznamu a program se vrátí do hlavního menu.

**Vstupní podmínky:** V seznamu existuje alespoň jeden úkol.

**Kroky testu:**

1. Spusťte program.

2. Přidejte alespoň jeden úkol (volba `1`).

3. Zadejte volbu `3`.

4. Na výzvu zadejte index `1` a potvrďte klávesou Enter.

**Očekávaný výsledek:** Program zobrazí zprávu o úspěšném smazání úkolu, úkol ze seznamu zmizí a program se vrátí do hlavního menu.

**Skutečný výsledek:** Program odstranil úkol číslo 1, zobrazil zprávu o úspěšném smazání a vrátil uživatele do hlavního menu. Úkol se již v seznamu nezobrazoval.

**Stav:** Pass 

**Poznámky:** Základní pozitivní test mazání.

---

## 5. Ukončení programu (Volba 4)

---

### TC25: Úspěšné ukončení aplikace volbou 4

**Název testovacího případu:** Korektní ukončení programu

**Popis:** Ověření, že volba číslo 4 bezpečně ukončí běžící skript bez dalšího zobrazování menu.

**Vstupní podmínky:** Program zobrazuje hlavní menu.

**Kroky testu:**

1. Spusťte program.

2. V hlavním menu zadejte možnost `4` a stiskněte Enter.

**Očekávaný výsledek:** Program vypíše rozloučení „Konec programu." a proces se úspěšně ukončí bez jakékoliv chybové hlášky. Hlavní menu se již nezobrazí.

**Skutečný výsledek:** Po zadání volby „4" program vypsal „Konec programu." a proces se ukončil bez chybových hlášek. Hlavní menu se nezobrazilo znovu.

**Stav:** Pass 

**Poznámky:** Základní ukončovací cyklus – menu se po volbě 4 nesmí znovu zobrazit.
