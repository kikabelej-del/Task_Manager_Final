# Projekt: Task Manager

Projekt vytvořený v rámci kurzu IT tester – Engeto.

## Popis programu

Program umožňuje správu úkolů prostřednictvím hlavního menu.
Úkoly jsou uloženy v seznamu a lze je přidávat, zobrazovat a odstraňovat.

## Funkce programu

- hlavni_menu() – zobrazí hlavní menu s volbami 1–4
- pridat_ukol() – přidá nový úkol se jménem a popisem, opakuje výzvu při prázdném vstupu
- zobrazit_ukoly() – vypíše všechny úkoly v seznamu
- odstranit_ukol() – odstraní úkol podle zadaného čísla

## Spuštění programu

Program se spouští v prostředí VS Code příkazem:

python projekt.task_manager.py

## Testování

Součástí projektu jsou testovací případy pokrývající:
- pozitivní testy – správné použití funkcí
- negativní testy – neplatné nebo prázdné vstupy
- hraniční případy – prázdný seznam, první a poslední úkol
