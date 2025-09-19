# Seznam, cykly for a while, podmínky

## Seznam

Datový typ list v Pythonu lze pomocí složených závorek (popřípadě pomocí `list()`).

Prázdný seznam:

```
seznam_a = [] 
```

Nový seznam s prvky:

```
dopravni_prostredky = ['auto', 'kolo', 'letadlo']
```

Počet prvků v seznamu:
```
print(len(dopravni_prostredky))
```

### Přistupování k prvkům pomocí indexu:
```
print(dopravni_prostredky[1])
print(dopravni_prostredky[-1])
print(dopravni_prostredky[0:2])
```

Podrobnosti: https://www.w3schools.com/python/python_lists.asp

## Cyklus for

Iterace přes pole:
```
for dp in dopravni_prostredky:
  print(dp)
```
Iterace s indexem:
```
for i in range(len(dopravni_prostredky)):
  print(dopravni_prostredky[i])
```

Iterace s indexem a prvkem:
```
for i, dp in enumerate(dopravni_prostredky):
  print(f'{i}: {dp}')
```

## Cyklus while

Využívá se hlavně, když není předem známo, kolik iterací bude.
```
i = 0
while i < len(dopravni_prostredky):
  print(dopravni_prostredky[i])
  i += 1
```

## Podmínky
```
if 'letadlo' in dopravni_prostredky:
  print('Poletíme!')
elif 'auto' in dopravni_prostredky or 'kolo' in dopravni_prostredky:
  print('Pojedeme.')
else:
  print('Půjdeme pěšky :-(')
```

## Předčasné ukončení cyklu nebo selé smyčky

```
i = 0
while i < len(dopravni_prostredky):
  if dopravni_prostredky[i] == 'kolo':
    break
  i += 1
```

## Úkoly

- Napište program, který sečte pouze pozitivní čísla v poli. [1, -2, 3, -4] → 4
- Napište program, který po zadání letopočtu vypíše století: 1705 → 18, 1900 → 19, 2000 → 20, 2024 → 21

