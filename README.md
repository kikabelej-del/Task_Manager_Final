# Správce úkolů (Task Manager)

Jednoduchá konzolová aplikace v jazyce Python určená pro efektivní správu každodenních úkolů. Umožňuje uživateli vytvářet nové úkoly, přehledně je zobrazovat a odstraňovat ty již splněné.

## Funkcionalita programu
1. **Přidat nový úkol:** Uživatel zadá název a popis úkolu. Vstupy jsou validovány proti prázdným hodnotám.
2. **Zobrazit všechny úkoly:** Vypíše přehledný, automaticky číslovaný seznam všech uložených úkolů.
3. **Odstranit úkol:** Umožňuje bezpečné smazání úkolu podle jeho pořadového čísla s kompletním ošetřením chybných číselných či textových vstupů.
4. **Konec programu:** Ukončení aplikace.

## Požadavky a spuštění
* **Požadavky:** Python verze 3.6 nebo vyšší.
* **Spuštění aplikace:**
  ```bash
  python task_manager.py