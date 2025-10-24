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

# Řešení

```python
def encrypt(text, key, offset = 1000):
    cypher = ''
    key_len = len(key)
    for index in range(len(text)):
        cypher += chr(ord(text[index]) + ord(key[index % key_len]) + offset)
    return cypher

def decrypt(cypher, key, offset = 1000):
    text = ''
    key_len = len(key)
    for index in range(len(cypher)):
        text += chr(ord(cypher[index]) - ord(key[index % key_len]) - offset)
    return text

t = 'jelenovi pivo nelej'
# t = 'Příliš žluťoučký kůň úpěl ďábelské ódy.'
k = 'tajne'

cypher = encrypt(t, k)
print(cypher)
original = decrypt(cypher, k)
print(original)
```

```python
import random

def generate_numbers(count, max):
    numbers = []
    for x in range(count):
        numbers.append(random.randint(0, max))
    return numbers

def create_histogram(numbers, bins):
    hist = [0] * bins
    for number in numbers:
        hist[number] += 1
    return hist

def draw_line(hist, line):
    print(f'{line:2d}', end=' ')
    for x in hist:
        if x >= line:
            print('*', end= '  ')
        else:
            print(' ', end= '  ')
    print('')

def draw_histogram(hist):
    lines = max(hist)
    for line in range(lines, 0, -1):
        draw_line(hist, line)
    print('  ', '  '.join([str(num) for num in range(10)]))
    print(' ', ' '.join([f'{num:2d}' for num in hist]))

numbers = generate_numbers(100, 9)
hist = create_histogram(numbers, 10)
draw_histogram(hist)
print(sum(hist))
```
