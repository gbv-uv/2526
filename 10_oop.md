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
    - Automobil bude mít atributy objem nádrže, spotřebu l/100 km, aktuální stav nádrže.
    - Metody pro tankování a ujetí x kilometrů.

## Řešení

```python
class Automobil:
    def __init__(self, objem_nadrze, spotreba, stav_nadrze):
        self.objem_nadrze = objem_nadrze
        self.spotreba = spotreba
        self.stav_nadrze = stav_nadrze
    
    def tankovat(self, litry):        
        nova_nadrz = self.stav_nadrze + litry
        if nova_nadrz > self.objem_nadrze:
            natankovano = self.objem_nadrze - self.stav_nadrze
            self.stav_nadrze = self.objem_nadrze
            print(f"Nádrž plná! Natankováno {natankovano:.1f} l")
        else:
            self.stav_nadrze = nova_nadrz
            print(f"Natankováno {litry:.1f} l")
    
    def trasa(self,kilometry):
        potreba = (kilometry / 100) * self.spotreba
        if potreba > self.stav_nadrze:
            max_km = (self.stav_nadrze / self.spotreba) * 100
            print(f"Nedostatek paliva! Lze ujet pouze {max_km:.1f} km")
            self.stav_nadrze = 0
        else:
            self.stav_nadrze -= potreba
            print(f"Ujeto {kilometry} km, zbývá {self.stav_nadrze:.1f} l paliva")
    
    def __str__(self):
        return f"Automobil (nádrž: {self.stav_nadrze:.1f}/{self.objem_nadrze} l, spotřeba: {self.spotreba} l/100km)"


auto = Automobil(objem_nadrze=50, spotreba=6.2, stav_nadrze=40)
print(auto)


auto1.tankovat(40)
print(auto)


auto.trasa(100)
auto.trasa(200)
auto.trasa(1000)
```
