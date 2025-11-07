# Externí moduly a balíčky

## Instalace externích balíčků (package)

Externí balíčky se instalují pomocí nástroje `pip`. Následující příkaz nainstaluje balíček `emoji`:

```
pip install emoji
```

Který je následně připraven k použití:

```
import emoji

message = emoji.emojize("Hello, Geek! :earth_americas:  :thumbs_up:", language='alias')
print(message)
```

Pro zobrazení podrobností o balíčku lze použít příkaz:

```
pip show emoji
```

Příkaz mimo jiné ukáže i cestu, kam se balíček nainstaloval.

Cesta k aktuálnímu Python interpeteru můžeme zobrazit pomocí scriptu:

``` python
import os, sys
os.path.dirname(sys.executable)
```

[Seznam dostupných emoji](https://www.webfx.com/tools/emoji-cheat-sheet/).

Pokud projekt používá více balíčků, je vhodné je zapsat do seznamu `requirements.txt` i s použitou verzí kvůli kompatibiltě:

```
BeautifulSoup==3.2.0
Django==1.3
Fabric==1.2.0
Jinja2==2.5.5
PyYAML==3.09
Pygments==1.4
SQLAlchemy==0.7.1
South==0.7.3
amqplib==0.6.1
anyjson==0.3
```

Balíčky pak lze nainstalovat jedním příkazem:

```
pip install -r requirements.txt
```

## Vytváření vlastních modulů

Modul se definuje do samostatného souboru s koncovkou `.py`. Příklad modulu pro převody mezi různými stupnicemi teplot `temperature.py`:

```python
def c_to_f(celsius):
    """Convert Celsius to Fahrenheit"""
    return (celsius * 9/5) + 32

def f_to_c(fahrenheit):
    """Convert Fahrenheit to Celsius"""
    return (fahrenheit - 32) * 5/9

def c_to_k(celsius):
    """Convert Celsius to Kelvin"""
    return celsius + 273.15

def k_to_c(kelvin):
    """Convert Kelvin to Celsius"""
    return kelvin - 273.15

def f_to_k(fahrenheit):
    """Convert Fahrenheit to Kelvin"""
    return (fahrenheit - 32) * 5/9 + 273.15

def k_to_f(kelvin):
    """Convert Kelvin to Fahrenheit"""
    return (kelvin - 273.15) * 9/5 + 32
```

Následné použití modulu:

```python
import temperature

print("25°C =", temperature.c_to_f(25), "°F")
print("25°C =", temperature.c_to_k(25), "K")
print("77°F =", temperature.f_to_c(77), "°C")
print("77°F =", temperature.f_to_k(77), "K")
print("300K =", temperature.k_to_c(300), "°C")
print("300K =", temperature.k_to_f(300), "°F")
```

Jméno modulu je odvozeno od názvu souboru.

## Úkoly

1. Vytvořete modul `calculator.py`, který bude obsahoval alespoň čtyři matematické funkce (například sčítání, odčítání...) a funkce z toho modulu použijte v souboru calc_usage.py
1. Nainstalujte si balíček Flask a zkuste si vytořit jednoduchý webový server. Příklad použití:

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
# ‘/’ URL is bound with hello_world() function.
def hello_world():
    return 'Hello World'

if __name__ == '__main__':

    app.run()
```

Stránka bude dostupná na adrese http://127.0.0.1:5000.
