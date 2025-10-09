# Funkce a datový typ slovník (dictionary)

## Funkce

Funkce má svoji definici, kde je uveden název, vstupní parametry (nemusí být žádný, nebo jich může být více), tělo a popřípadě return pro vrácení hodnoty.

Vysvětlení s více příkaldy [zde](https://www.w3schools.com/python/python_functions.asp).

```python
def obvod_kruznice (polomer):
    obvod = 2 * 3.14 * polomer
return obvod
```


## Slovník (dictionary)

Slovník slouží k ukládání párů hodnot - klíč: hodnota.

Podrobnosti například [zde](https://www.w3schools.com/python/python_dictionaries.asp).

```pyton
student = {'jmeno': 'Jan',
           'prijmeni': 'Novák'
           'vek': 18,
           'premiant': True
｝
print(student['jmeno'])
```

# Příklady k procvičení
1. Napište funkci, pro výpočet obsahu obdélníku.
1. Napište program, který bude sloužit jako databáze studentů. Bude použit slovník, kde klíč bude studentovo jméno a hodnota pole s jeho známkami. Program bude umět přidávat známky a počítat aktuální průměry.
