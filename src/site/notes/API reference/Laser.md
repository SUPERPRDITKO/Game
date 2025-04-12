---
{"dg-publish":true,"permalink":"/api-reference/laser/"}
---

# 🔫 Modul `laser`

## Popis

Tento modul slouží k ovládání laserového modulu připojeného k micro:bitu. Pomocí PWM (analogového výstupu) lze laser zapnout, vypnout nebo aktivovat na předem definovanou dobu jako výstřel.

---

## Třída `Laser(pin=pin0, power=512)`

```python
l = laser.Laser(pin=pin0, power=512)
```

**Popis:**

Inicializuje laserový modul na daném pinu s danou intenzitou výkonu (PWM).

### Parametry:

- `pin` (`pin`) – výstupní pin micro:bitu, na který je laser připojen (např. `pin0`)
    
- `power` (`int`) – hodnota PWM signálu v rozsahu 0–1023 (vyšší hodnota = vyšší intenzita)
    

---

## Metody

### `on()`

```python
l.on()
```

Zapne laser s přednastaveným výkonem.

---

### `off()`

```python
l.off()
```

Vypne laser – pin se nastaví na digitální hodnotu 0.

---

### `shoot(duration=500)`

```python
l.shoot(300)
```

Zapne laser na zadaný počet milisekund a poté jej vypne.

**Parametry:**

- `duration` (`int`) – délka svícení laseru v milisekundách (výchozí je 500 ms)
    

---

## Ukázkový kód

```python
from microbit import *
from easymb import laser  # Třída Laser je uložena v souboru laser.py

l = laser.Laser(pin0, 800)  # Laser na pinu 0 s výkonem 800

while True:
    if button_a.was_pressed():
        l.shoot(300)  # Krátký výstřel při stisku tlačítka A
    sleep(50)
```

**Popis chování:**

- Laser je připojen na `pin0` a má nastavenou intenzitu 800.
    
- Při stisku tlačítka A se aktivuje metoda `shoot()`, která laser zapne na 300 ms a pak automaticky vypne.
    
[[API reference/Api home\|Api home]]