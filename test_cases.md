"""
Program pro Projekt: Task manager
Umožňuje přidávat, zobrazovat a odstraňovat úkoly uložené v seznamu.
Každý úkol je uložen jako slovník s klíči 'nazev' a 'popis'.
"""


def hlavni_menu():
    """
    Zobrazí hlavní menu programu s volbami 1–4.
    """
    print("\nSprávce úkolů - Hlavní menu")
    print("1. Přidat nový úkol")
    print("2. Zobrazit všechny úkoly")
    print("3. Odstranit úkol")
    print("4. Konec programu")


def zobrazit_ukoly(ukoly):
    """
    Vypíše všechny úkoly v seznamu s jejich pořadovým číslem.
    Pokud je seznam prázdný, informuje uživatele a vrátí False.
    Využívá enumerate pro automatické číslování od 1.

    Parametry:
        ukoly (list): Seznam slovníků s klíči 'nazev' a 'popis'.

    Vrací:
        bool: True pokud seznam obsahuje úkoly, jinak False.
    """
    if not ukoly:
        print("Seznam úkolů je prázdný.")
        return False

    print("\nSeznam úkolů:")
    for i, ukol in enumerate(ukoly, start=1):
        print(f"{i}. {ukol['nazev']} - {ukol['popis']}")
    return True


def pridat_ukol(ukoly):
    """
    Požádá uživatele o název a popis nového úkolu.
    Opakuje výzvu pomocí smyčky while, dokud uživatel nezadá neprázdný vstup.
    Přidá nový úkol jako slovník do seznamu.

    Parametry:
        ukoly (list): Seznam úkolů, do kterého bude nový úkol přidán.

    Vrací:
        list: Aktualizovaný seznam úkolů.
    """
    while True:
        nazev = input("Zadejte název úkolu: ").strip()
        if nazev:
            break
        print("Neplatná volba, zkuste to znovu.")

    while True:
        popis = input("Zadejte popis úkolu: ").strip()
        if popis:
            break
        print("Neplatná volba, zkuste to znovu.")

    novy_ukol = {"nazev": nazev, "popis": popis}
    ukoly.append(novy_ukol)
    print(f"Úkol '{nazev}' byl úspěšně přidán.")
    return ukoly


def odstranit_ukol(ukoly):
    """
    Zobrazí seznam úkolů a umožní uživateli jeden úkol odstranit podle čísla.
    Opakuje výzvu pomocí smyčky while při neplatném vstupu.
    Obsahuje validaci prázdného seznamu, rozsahu a typu vstupu.

    Parametry:
        ukoly (list): Seznam úkolů, ze kterého bude úkol odstraněn.

    Vrací:
        list: Aktualizovaný seznam úkolů.
    """
    if not zobrazit_ukoly(ukoly):
        return ukoly

    while True:
        try:
            index = int(input("Zadejte číslo úkolu, který chcete odstranit: "))
            if 1 <= index <= len(ukoly):
                odstraneny = ukoly.pop(index - 1)
                print(f"Úkol '{odstraneny['nazev']}' byl odstraněn.")
                break
            else:
                print("Neplatná volba, zkuste to znovu.")
        except ValueError:
            print("Neplatná volba, zkuste to znovu.")

    return ukoly


def main():
    """
    Hlavní funkce programu.
    Spouští hlavní smyčku, která zobrazuje menu a zpracovává volby uživatele,
    dokud uživatel nezvolí konec programu (volba 4).
    """
    ukoly = []

    while True:
        hlavni_menu()
        volba = input("Vyberte možnost (1-4): ").strip()

        if volba == "1":
            ukoly = pridat_ukol(ukoly)
        elif volba == "2":
            zobrazit_ukoly(ukoly)
        elif volba == "3":
            ukoly = odstranit_ukol(ukoly)
        elif volba == "4":
            print("Konec programu.")
            break
        else:
            print("Neplatná volba, zkuste to znovu (zadejte 1-4).")


if __name__ == "__main__":
    main()