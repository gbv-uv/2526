# Pokračování konceptů objektově orientovaného programování


## Abstrakce

Abstrakce je princip objektově orientovaného programování, který umožňuje definovat obecnou šablonu (abstraktní třídu) s metodami bez konkrétní implementace, kterou musí doplnit podtřídy. Skrývá složité detaily implementace a definuje pouze základní rozhraní, které musí všechny potomci dodržet.

## Polymorfismus

Polymorfismus je princip objektově orientovaného programování, který umožňuje různým třídám implementovat stejné metody různými způsoby, přičemž lze s nimi pracovat jednotně přes společné rozhraní. Díky tomu můžeme volat stejnou metodu na různých objektech a každý objekt se chová podle své vlastní implementace.

## Kompozice

Kompozice je princip objektově orientovaného programování, kdy třída obsahuje instance jiných tříd jako své atributy (vztah "má", has-a), místo aby je dědila. Umožňuje vytvářet složité objekty skládáním menších, nezávislých komponent, což vede k flexibilnějšímu a znovupoužitelnějšímu kódu než dědění.

```python
from datetime import datetime
from abc import ABC, abstractmethod

class ClenSkoly(ABC):
    def __init__(self, jmeno, prijmeni, datum_narozeni):
        self.jmeno = jmeno
        self.prijmeni = prijmeni
        self._datum_narozeni = datetime.strptime(datum_narozeni, "%d. %m. %Y")
    
    def cele_jmeno(self):
        return f'{self.jmeno} {self.prijmeni}'
    
    def vek(self):
        return (datetime.now() - self._datum_narozeni).days // 365
    
    @abstractmethod
    def cele_info(self):
        pass
    
    @abstractmethod
    def role(self):
        pass

class Adresa:
    def __init__(self, ulice, mesto, psc):
        self.ulice = ulice
        self.mesto = mesto
        self.psc = psc
    
    def __str__(self):
        return f'{self.ulice}, {self.psc} {self.mesto}'

class Predmet:
    def __init__(self, nazev, ucitel):
        self.nazev = nazev
        self.ucitel = ucitel
    
    def __str__(self):
        return f'{self.nazev} (vyučuje: {self.ucitel})'

class Osoba(ClenSkoly):
    def __init__(self, jmeno, prijmeni, datum_narozeni, adresa=None):
        super().__init__(jmeno, prijmeni, datum_narozeni)
        self.adresa = adresa
    
    def cele_info(self):
        info = f'{self.jmeno} {self.prijmeni} {self.vek()} let'
        if self.adresa:
            info += f', bydliště: {self.adresa}'
        return info
    
    def role(self):
        return "Člen školy"

class Student(ClenSkoly):
    def __init__(self, jmeno, prijmeni, datum_narozeni, trida, adresa=None):
        super().__init__(jmeno, prijmeni, datum_narozeni)
        self.trida = trida
        self.adresa = adresa
        self.predmety = []
    
    def pridej_predmet(self, predmet):
        self.predmety.append(predmet)
    
    def cele_info(self):
        info = f'{self.jmeno} {self.prijmeni} {self.vek()} let, třída: {self.trida}'
        if self.adresa:
            info += f', bydliště: {self.adresa}'
        if self.predmety:
            info += f'\n  Předměty: {", ".join([p.nazev for p in self.predmety])}'
        return info
    
    def role(self):
        return "Student"

class Ucitel(ClenSkoly):
    def __init__(self, jmeno, prijmeni, datum_narozeni, aprobace, adresa=None):
        super().__init__(jmeno, prijmeni, datum_narozeni)
        self.aprobace = aprobace  # seznam předmětů, které vyučuje
        self.adresa = adresa
    
    def cele_info(self):
        info = f'{self.jmeno} {self.prijmeni} {self.vek()} let, vyučuje: {", ".join(self.aprobace)}'
        if self.adresa:
            info += f', bydliště: {self.adresa}'
        return info
    
    def role(self):
        return f"Učitel ({', '.join(self.aprobace)})"

adresa1 = Adresa('Hlavní 123', 'Praha', '11000')
adresa2 = Adresa('Školní 45', 'Brno', '60200')
adresa3 = Adresa('Nová 78', 'Ostrava', '70200')

petr = Osoba('Petr', 'Dohnal', '11. 5. 2001', adresa1)
tonda = Osoba('Antonín', 'Novák', '13. 12. 2007', adresa2)

ucitel_matematika = Ucitel('Marie', 'Svobodová', '15. 3. 1985', ['Matematika', 'Fyzika'], adresa3)
ucitel_cestina = Ucitel('Josef', 'Dvořák', '22. 8. 1978', ['Čeština', 'Dějepis'])

matematika = Predmet('Matematika', 'Marie Svobodová')
fyzika = Predmet('Fyzika', 'Marie Svobodová')
cestina = Predmet('Čeština', 'Josef Dvořák')

jan = Student('Jan', 'Burget', '13. 12. 2009', '5.A', adresa2)
jan.pridej_predmet(matematika)
jan.pridej_predmet(fyzika)
jan.pridej_predmet(cestina)

print("=== Informace o členech školy ===")
print(petr.cele_info())
print(tonda.cele_info())
print(jan.cele_info())
print(ucitel_matematika.cele_info())
print(ucitel_cestina.cele_info())

print("\n=== Role ve škole (polymorfismus) ===")
clenove = [petr, tonda, jan, ucitel_matematika, ucitel_cestina]
for clen in clenove:
    print(f'{clen.cele_jmeno()}: {clen.role()}')
```
