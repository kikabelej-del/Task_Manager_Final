# Testovací scénáře pro aplikaci Správce úkolů (Task Manager)

Tento dokument obsahuje kompletní sadu detailních testovacích případů (TC) pro ověření funkčnosti aplikace podle stanoveného zadání.

---

## 1. Funkce: hlavni_menu (Navigace a validace volby)

### TC01: Výběr platné možnosti z menu
* **Název testovacího případu:** Výběr platné možnosti z menu
* **Popis:** Ověření, že volba čísla 1 v hlavním menu správně spustí funkci pridat_ukol.
* **Vstupní podmínky:** Program zobrazuje hlavní menu.
* **Kroky testu:** *
  1. Spusťte program.
  2. Ověřte, že se zobrazuje hlavní menu s nabídkou voleb (1-4).
  3. Zadejte číslo 1.
  4. Potvrďte stisknutím klávesy Enter.
* **Očekávaný výsledek:** Program spustí funkci pridat_ukol() a vyzve uživatele k zadání názvu úkolu.
* **Skutečný výsledek:** Funkce pridat_ukol() byla spuštěna a program zobrazil výzvu k zadání nového úkolu.
* **Stav:** Pass
* **Poznámky:** Ověřuje základní navigaci z hlavního menu.

### TC02: Zadání neplatného vstupu v hlavním menu (písmeno)
* **Název testovacího případu:** Zadání textu místo čísla volby
* **Popis:** Ověření, že program nespadne, pokud uživatel zadá neplatný znak (písmeno) a znovu zobrazí menu.
* **Vstupní podmínky:** Program zobrazuje hlavní menu.
* **Kroky testu:**
  1. Do výzvy pro výběr volby zadejte písmeno "ABC".
  2. Potvrďte klávesou Enter.
* **Očekávaný výsledek:** Program zobrazí chybové hlášení o neplatné volbě, nespadne a znovu vypíše hlavní menu.
* **Skutečný výsledek:** Program vypsal chybovou hlášku a zopakoval menu.
* **Stav:** Pass
* **Poznámky:** Test robustnosti proti nesprávnému typu dat.

---

## 2. Funkce: pridat_ukol (Vytváření úkolů)

### TC03: Úspěšné přidání úkolu s platným názvem a popisem
* **Název testovacího případu:** Přidání běžného úkolu do seznamu
* **Popis:** Ověření, že systém správně vytvoří a uloží úkol s validními údaji.
* **Vstupní podmínky:** Seznam úkolů je prázdný.
* **Kroky testu:**
  1. V menu zvolte možnost 1.
  2. Na výzvu "Zadejte název úkolu:" zadejte text "Koupit kytky".
  3. Na výzvu "Zadejte popis úkolu:" zadejte text "Vzít červené růže".
  4. Potvrďte klávesou Enter.
* **Očekávaný výsledek:** Program zobrazí potvrzení o úspěšném přidání úkolu a vrátí uživatele do hlavního menu.
* **Skutečný výsledek:** Zobrazila se zpráva, že úkol byl úspěšně přidán.
* **Stav:** Pass
* **Poznámky:** Základní pozitivní scénář.

### TC04: Pokus o zadání prázdného názvu úkolu
* **Název testovacího případu:** Validace prázdného vstupu u názvu úkolu
* **Popis:** Ověření, že program nepovolí vytvořit úkol bez názvu.
* **Vstupní podmínky:** Spuštěná funkce pro přidání úkolu.
* **Kroky testu:**
  1. Do políčka "Zadejte název úkolu:" nezadávejte nic a stiskněte pouze klávesu Enter.
* **Očekávaný výsledek:** Program zobrazí varování, že název nemůže být prázdný, a nepustí uživatele dál, dokud název nevyplní.
* **Skutečný výsledek:** Program detekoval prázdný vstup, zobrazil chybu a opakuje výzvu pro název.
* **Stav:** Pass
* **Poznámky:** Negativní test na povinné pole.

### TC05: Pokus o zadání prázdného popisu úkolu
* **Název testovacího případu:** Validace prázdného vstupu u popisu úkolu
* **Popis:** Ověření, že program nepovolí vytvořit úkol s prázdným popisem.
* **Vstupní podmínky:** Zadaný platný název úkolu.
* **Kroky testu:**
  1. Do políčka "Zadejte popis úkolu:" nezadávejte nic a stiskněte Enter.
* **Očekávaný výsledek:** Program zobrazí varování, že popis nemůže být prázdný, a vyžaduje zadání znovu.
* **Skutečný výsledek:** Program zobrazil chybu a opakuje výzvu pro popis.
* **Stav:** Pass
* **Poznámky:** Negativní test na validaci popisu.

### TC06: Zadání názvu úkolu se speciálními znaky a číslicemi
* **Název testovacího případu:** Podpora speciálních znaků ve vstupu
* **Popis:** Ověření, že systém správně uloží a zobrazí znaky jako @, #, $, 123.
* **Vstupní podmínky:** Spuštěná funkce pro přidání úkolu.
* **Kroky testu:**
  1. Jako název zadejte "Projekt #1 @Online".
  2. Jako popis zadejte "Cena: 50$".
  3. Potvrďte a uložte.
* **Očekávaný výsledek:** Úkol je úspěšně uložen bez kódovacích chyb.
* **Skutečný výsledek:** Úkol byl uložen a text se zobrazuje korektně.
* **Stav:** Pass
* **Poznámky:** Test znakové sady a kódování textu.

### TC07: Přidání duplicitního úkolu (stejný název)
* **Název testovacího případu:** Vytvoření úkolu se stejným názvem
* **Popis:** Ověření, jak se systém chová při zadání úkolu, který již existuje.
* **Vstupní podmínky:** V seznamu již existuje úkol "Koupit kytky".
* **Kroky testu:**
  1. Spusťte přidání úkolu.
  2. Zadejte název "Koupit kytky".
  3. Zadejte popis "Vzít modré růže".
  4. Uložte úkol.
* **Očekávaný výsledek:** Program úkol přidá jako novou položku (jelikož systém umožňuje více úkolů se stejným názvem, ale odlišným ID/indexem).
* **Skutečný výsledek:** Úkol byl úspěšně přidán pod novým pořadovým číslem.
* **Stav:** Pass
* **Poznámky:** Ověření logiky duplicitních dat.

---

## 3. Funkce: zobrazit_ukoly (Výpis dat)

### TC08: Zobrazení seznamu s uloženými úkoly
* **Název testovacího případu:** Kontrola formátu zobrazení úkolů
* **Popis:** Ověření, že se úkoly vypisují s automatickým číslováním od indexu 1 ve formátu Název - Popis.
* **Vstupní podmínky:** V systému jsou uloženy dva úkoly.
* **Kroky testu:**
  1. V hlavním menu zvolte možnost 2 (Zobrazit úkoly).
* **Očekávaný výsledek:** Zobrazí se seznam úkolů, kde každý řádek začíná správným pořadovým číslem (1, 2) následovaným názvem a popisem.
* **Skutečný výsledek:** Úkoly se vypsaly přehledně se správným indexováním.
* **Stav:** Pass
* **Poznámky:** Základní pozitivní test zobrazení.

### TC09: Pokus o zobrazení seznamu, pokud je prázdný
* **Název testovacího případu:** Kontrola výpisu při nulovém počtu úkolů
* **Popis:** Ověření, že program korektně informuje uživatele, pokud v systému nejsou žádná data.
* **Vstupní podmínky:** Seznam úkolů je zcela prázdný.
* **Kroky testu:**
  1. V hlavním menu zadejte volbu 2.
  2. Potvrďte Enter.
* **Očekávaný výsledek:** Program zobrazí jasný text: "Seznam úkolů je prázdný."
* **Skutečný výsledek:** Vypisuje text o prázdném seznamu.
* **Stav:** Pass
* **Poznámky:** Hraniční stav systému.

---

## 4. Funkce: odstranit_ukol (Mazání dat a indexace)

### TC10: Úspěšné odstranění existujícího úkolu
* **Název testovacího případu:** Odstranění úkolu zadáním platného čísla
* **Popis:** Ověření, že vybraný úkol je ze systému trvale odstraněn.
* **Vstupní podmínky:** V seznamu existuje úkol pod číslem 1.
* **Kroky testu:**
  1. V hlavním menu zvolte možnost 3 (Odstranit úkol).
  2. Na výzvu zadejte index 1 a potvrďte.
* **Očekávaný výsledek:** Program zobrazí zprávu o úspěšném smazání úkolu a úkol ze seznamu zmizí.
* **Skutečný výsledek:** Úkol byl úspěšně odstraněn.
* **Stav:** Pass
* **Poznámky:** Základní pozitivní test mazání.

### TC11: Pokus o odstranění úkolu, pokud je seznam prázdný
* **Název testovacího případu:** Mazání v prázdném stavu
* **Popis:** Ověření, že program uživateli nedovolí zadat číslo ke smazání, pokud v systému nic není.
* **Vstupní podmínky:** Seznam úkolů je prázdný.
* **Kroky testu:**
  1. V hlavním menu zvolte možnost 3.
* **Očekávaný výsledek:** Program hned po spuštění funkce vypíše, že seznam je prázdný a není co mazat, a vrátí se do menu.
* **Skutečný výsledek:** Program detekoval prázdný stav a nepovolil zadat index.
* **Stav:** Pass
* **Poznámky:** Ošetření logického toku aplikace.

### TC12: Zadání neexistujícího čísla úkolu (mimo rozsah)
* **Název testovacího případu:** Pokus o smazání úkolu mimo rozsah indexů
* **Popis:** Ošetření chybové zprávy při zadání neexistujícího čísla.
* **Vstupní podmínky:** V systému je uložen pouze 1 úkol (index 1).
* **Kroky testu:**
  1. Spusťte funkci pro odstranění úkolu.
  2. Jako číslo úkolu ke smazání zadejte hodnotu 5.
* **Očekávaný výsledek:** Program nesmí spadnout s chybou. Musí zachytit neplatný index, vypsat chybu a nechat uživatele zadat číslo znovu.
* **Skutečný výsledek:** Program zobrazil upozornění na neplatné číslo úkolu a vyžádal si správný vstup.
* **Stav:** Pass
* **Poznámky:** Negativní test na validaci číselného rozsahu.

### TC13: Zadání neplatného vstupu namísto čísla (písmeno)
* **Název testovacího případu:** Validace datového typu při mazání
* **Popis:** Ošetření chybové zprávy ValueError při zadání textu namísto čísla úkolu.
* **Vstupní podmínky:** V systému jsou uloženy úkoly.
* **Kroky testu:**
  1. Spusťte volbu 3 (Odstranit úkol).
  2. Do výzvy pro číslo úkolu zadejte text "abc".
* **Očekávaný výsledek:** Program zachytí nesprávný datový typ, nespadne a zobrazí zprávu: "Neplatná volba, zkuste to znovu."
* **Skutečný výsledek:** Chyba byla zachycena, program bezpečně pokračuje a opakuje výzvu.
* **Stav:** Pass
* **Poznámky:** Důležitý test stability kódu.

### TC14: Ověření přepočítání indexů po smazání
* **Název testovacího případu:** Kontrola přeindexování zbylých úkolů
* **Popis:** Ověření, že po smazání úkolu číslo 1 se původní úkol číslo 2 posune na index 1.
* **Vstupní podmínky:** V systému jsou uloženy dva úkoly (1. Úkol A, 2. Úkol B).
* **Kroky testu:**
  1. Odstraňte úkol číslo 1 (Úkol A).
  2. Spusťte volbu 2 (Zobrazit úkoly).
* **Očekávaný výsledek:** V seznamu zůstane pouze jeden úkol (Úkol B) a bude správně očíslován jako číslo 1.
* **Skutečný výsledek:** Seznam se správně přeindexoval od jedničky.
* **Stav:** Pass
* **Poznámky:** Test integrity a správného chování datové struktury.

---

## 5. Ukončení programu (Volba 4)

### TC15: Úspěšné ukončení aplikace volbou z menu
* **Název testovacího případu:** Korektní ukončení programu
* **Popis:** Ověření, že volba číslo 4 bezpečně ukončí běžící skript.
* **Vstupní podmínky:** Program zobrazuje hlavní menu.
* **Kroky testu:**
  1. V hlavním menu zadejte možnost 4 a stiskněte Enter.
* **Očekávaný výsledek:** Program vypíše rozloučení (např. "Konec programu.") a proces se úspěšně ukončí bez jakékoliv chybové hlášky.
* **Skutečný výsledek:** Program se rozloučil a korektně zavřel konzoli.
* **Stav:** Pass
* **Poznámky:** Základní ukončovací cyklus.

---

## 6. Datová validace a robustnost

### TC16: Testování extrémní délky řetězce na vstupu
* **Název testovacího případu:** Vložení extrémně dlouhého textu
* **Popis:** Ověření stability programu, pokud uživatel zadá text o délce více než 50 znaků do názvu/popisu.
* **Vstupní podmínky:** Spuštěná funkce pro přidání úkolu.
* **Kroky testu:**
  1. Do pole název vložte opakující se text o délce 50 znaků.
  2. Uložte úkol a následně jej zobrazte přes volbu 2.
* **Očekávaný výsledek:** Program text bez problému zpracuje, nespadne na přetečení paměti a úkol uloží.
* **Skutečný výsledek:** Úkol byl úspěšně uložen a celý dlouhý text se vypsal na obrazovku.
* **Stav:** Pass
* **Poznámky:** Zátěžový test (Stress test).

### TC17: Ověření chování při zadání záporného čísla úkolu
* **Název testovacího případu:** Validace záporných hodnot u indexu úkolu
* **Popis:** Ověření, jak systém reaguje na zadání záporného čísla (např. -1) při mazání úkolu.
* **Vstupní podmínky:** V systému existují úkoly.
* **Kroky testu:**
  1. Přejděte do volby 3 (Odstranit úkol).
  2. Jako číslo úkolu zadejte hodnotu -1.
* **Očekávaný výsledek:** Program vyhodnotí záporné číslo jako neplatný vstup, odmítne úkol smazat a vyzve uživatele k zadání platného kladného čísla.
* **Skutečný výsledek:** Systém zobrazil chybovou hlášku a záporné číslo neakceptoval.
* **Stav:** Pass
* **Poznámky:** Hraniční test pro ošetření logických chyb indexování v Pythonu.
