# Moduly

Moduly seskupují fukne a objekty, které je možné opakovaně využít v programech.

Některé moduly jsou již obsaženy ve výchozí instalaci Pythonu, některé jiné je potřeba doinstalovat pomocí instalátoru balíčků pip. Popřípadě je možné si vytvořit vlasní modul.

## Matematický modul `math`

Jako pžíklad předinstalovaného modulu si ukážeme práci s modulem `math`.

Nejprve je potřeba modul importovat:

```python
import math
```

Modul obsahuje funkce a konstanty, jejich přehled lze najít například v [dokumentaci](https://docs.python.org/3/library/math.html).

Použítí funkce a konstanty:

```python
import math

obsah_kruhu = math.pi * math.pow(3, 2)
```

Stejný program, ale místo celého modulu se importuje přímo konstanta a funkce:

```python
from math import pi, pow

obsah_kruhu = pi * pow(3, 2)
```
