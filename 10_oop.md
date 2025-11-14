# Objektově orientované programování

Objektově orientované programování je stejně jako procedurální nebo funcionální programování přístup k organizaci a členění zdrojového kódu.

## Pojmy
- Objekt
- Třída
- Atribut
- Metoda
- Konstruktor

## Zápis třídy v Pythonu

```python
class Osoba:
    def __init__(self, jmeno, prijmeni):          # konstruktor
        self.jmeno =  jmeno                       # deklarace atributu
        self.prijmeni = prijmeni

    def cele_jmeno(self):                         # metoda 
        return f'{self.jmeno} {self.prijmeni}'
```

## Práce s datem v Pythonu

Vypsání aktuálního času:

```python
import datetime

x = datetime.datetime.now()

print(x)
print(x.year)
print(x.strftime("%A"))
```

Více příkladů pro formátování času lze najít například [zde](https://www.geeksforgeeks.org/python/python-datetime-strptime-function/).

Načítání času:

```python
import datetime

date = datetime.datetime.strptime('21. 11. 2025', "%d. %m. %Y")
print(date)
```

Výpočet aktuálního věku:

```python
import datetime

date = datetime.datetime.strptime('20. 2. 1991', "%d. %m. %Y")
now = datetime.datetime.now()
print((now - date).days // 365)
```

## Úkoly

- Navrhněte třídu pro automobily a použijte ji obdobně jako v příkladu s osobami.
