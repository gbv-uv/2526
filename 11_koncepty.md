# Koncepty objektově orientovaného programování

## Dědičnost

Nová třída může zdědit atributy a metody z jiné (rodičovské) třídy.

```pyhton
from datetime import datetime

class Osoba:
    def __init__(self, jmeno, primeni, datum_narozeni):
        self.jmeno = jmeno
        self.prijmeni = primeni
        self.datum_narozeni = datetime.strptime(datum_narozeni, "%d. %m. %Y")
    def cele_jmeno(self):
        return f'{self.jmeno} {self.prijmeni}'
    def cele_info(self):
        return f'{self.jmeno} {self.prijmeni} {self.vek()} let'
    def vek(self):
        return (datetime.now() - self.datum_narozeni).days // 365
    
class Student(Osoba):
    def __init__(self, jmeno, primeni, datum_narozeni, trida):
        super().__init__(jmeno, primeni, datum_narozeni)
        self.trida = trida

petr = Osoba('Petr', 'Dohnal', '11. 5. 2001')
tonda = Osoba('Antonín', 'Novák', '13. 12. 2007')
jan = Student('Jan', 'Burget', '13. 12. 2009', '5.A')
print(petr.cele_info())
print(tonda.cele_info())
print(jan.cele_info())
```

## Zapouzdření

Skrytí atributů před přímým přístupem, dají se získat a zapsat pomocí metod.
Atributy `private` se definují se dvěma podtržítky na začátku `self.__datum_narozeni` a mělo by se k nim přistupovat přímo pouze v rámci třídy, atributy `protected` se definují s jedním podtržítkem `self._trida` a mohou k nim přistupovat i třídy, které z této třídy dědily.

```python
from datetime import datetime

class Osoba:
    def __init__(self, jmeno, primeni, datum_narozeni):
        self.jmeno = jmeno
        self.prijmeni = primeni
        self.__datum_narozeni = datetime.strptime(datum_narozeni, "%d. %m. %Y")
    def cele_jmeno(self):
        return f'{self.jmeno} {self.prijmeni}'
    def cele_info(self):
        return f'{self.jmeno} {self.prijmeni} {self.vek()} let'
    def datum_narozeni(self):
        return self.__datum_narozeni
    def vek(self):
        return (datetime.now() - self.datum_narozeni).days // 365
    
class Student(Osoba):
    def __init__(self, jmeno, primeni, datum_narozeni, trida):
        super().__init__(jmeno, primeni, datum_narozeni)
        self.trida = trida

petr = Osoba('Petr', 'Dohnal', '11. 5. 2001')
tonda = Osoba('Antonín', 'Novák', '13. 12. 2007')
jan = Student('Jan', 'Burget', '13. 12. 2009', '5.A')
print(petr.cele_info())
print(tonda.cele_info())
print(jan.cele_info())
```
