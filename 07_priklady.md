# Další série příkladů na procvičení

1. Napište funkce pro šifrování a dešifrování textu pomocí klíče. Pro převod písmene na číslo můžete použít funkce `ord('A')` -≥ 65 a zpět `chr(65)` -≥ 'A'.
1. Napište funkci, která vygeneruje seznam 100 náhodných čísel v rozmezí 0 - 9. Pro generování náhodných čísel je potřeba importovat knihovnu `random` a následně použít funkci `randint()`:
   ```python
   import random
   random.randint(0,10)
   ```
1. Ze seznamu z předchozího úkolu uděljete histogram a vytiskněte ho do konzole. Například histogram pro seznam [0, 0, 0, 1, 1, 2, 2, 2, 2, 3, 5, 5] by vypadal následovně:
   ```
       *
   *   *
   * * *     *
   * * * *   *
   ```
