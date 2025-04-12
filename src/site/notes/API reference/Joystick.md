---
{"dg-publish":true,"permalink":"/api-reference/joystick/"}
---

# `joystick` – čtení hodnot z analogového joysticku

Třída `joystick` obsahuje statickou metodu pro načtení hodnot z analogového joysticku připojeného k micro:bitu pomocí dvou analogových vstupů.

## Metody

### `GetXY(pinX, pinY, screen)`

Vrátí aktuální polohu joysticku ve směru osy X a Y.

```python
joystick.GetXY(pinX, pinY, screen)
```

#### Parametry

- `pinX` – analogový pin připojený k ose **X** joysticku (např. `pin1`)
    
- `pinY` – analogový pin připojený k ose **Y** joysticku (např. `pin2`)
    
- `screen` – logická hodnota (`True` / `False`)
    
    - Pokud je `True`, vrací hodnoty převedené na rozsah **0 až 4** (např. pro zobrazení na LED matici 5×5).
        
    - Pokud je `False`, vrací plnou hodnotu z analogového čtení v rozsahu **0 až 1023**.
        

#### Návratová hodnota

- Dvojice `(x, y)` – aktuální pozice joysticku na ose X a Y, buď v rozsahu 0–1023 nebo 0–4 podle volby `screen`.
    

---

## Ukázkový kód

```python
from microbit import *
from easymb import joystick  # Pokud je ve zvláštním souboru

while True:
    x, y = joystick.GetXY(pin1, pin2, screen=True)
    display.clear()
    display.set_pixel(x, y, 9)  # Zobrazí pozici joysticku na LED matici
    sleep(100)
```

🛈 **Poznámka:** Pokud joystick nefunguje správně, ověř, že jsou piny správně připojeny a analogové výstupy joysticku nejsou zkráceny na GND.

[[API reference/Api home\|Api home]]