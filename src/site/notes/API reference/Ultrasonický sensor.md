---
{"dg-publish":true,"permalink":"/api-reference/ultrasonicky-sensor/"}
---

# `ultraSonic` – měření vzdálenosti ultrazvukovým senzorem

Třída `ultraSonic` obsahuje statickou metodu pro čtení vzdálenosti z jednoduchého ultrazvukového senzoru, který poskytuje analogový výstup (např. **HC-SR04 s analogovým převodníkem**, nebo obdobné senzory s analogovým výstupem).

## Metody

### `read_distance_cm(signal)`

Vrací aktuálně naměřenou vzdálenost ve **centimetrech**.

```python
ultraSonic.read_distance_cm(signal)
```

#### Parametry

- `signal` – analogový pin připojený k výstupu senzoru (např. `pin3`, `pin4`, `pin10`)
    

#### Návratová hodnota

- Vzdálenost v centimetrech (typ `float`)
    

---

### Ukázkový kód

```python
from microbit import *
from easymb import ultraSonic


while True:
	# Upozornění: displej micro:bitu by měl být vypnutý
	display.off()
    vzdalenost = ultraSonic.read_distance_cm(pin3)
    
    sleep(100) # Pouze pro jistotu, nemělo by být nutné
    display.on()
    display.scroll("Vzdálenost: {:.1f} cm".format(vzdalenost)) 
```

---

## Důležitá upozornění

⚠️ **Používejte pouze piny `pin3`, `pin4` nebo `pin10`!** Ostatní piny nemají dostatečně přesné ADC nebo mohou být interně připojené k jiným komponentám.

⚠️ **Vypni displej pomocí `display.off()`**, jinak může docházet k rušení a zkreslení výsledků měření.

🛈 Pokud senzor vrací stále vysoké hodnoty nebo nulu, zkontroluj napájení senzoru a správnost analogového výstupu.

[[API reference/Api home\|Api home]]