---
{"dg-publish":true,"permalink":"/api-reference/motory/"}
---

# `motor` – ovládání serva

Třída `motor` poskytuje metody pro řízení servomotoru a jednoduchého auta pomocí tří  pinů micro:bitu.

## Třída `motor.servo`

Tato vnořená třída umožňuje ovládat běžný **servomotor** pomocí analogového signálu.

### `driveServo(pin, num)`

Nastaví polohu servomotoru.

```python
motor.servo.driveServo(pin, num)
```

#### Parametry

- `pin` – pin připojený k ovládání serva (např. `pin0`)
    
- `num` – hodnota od 0 do 1024, kde:
    
    - 0 = minimální pozice (např. 0°)
        
    - 1024 = maximální pozice (např. 180°)
        

#### Návratová hodnota

- `True` při úspěchu.
    

#### Výjimky

- `ValueError` – pokud je hodnota mimo rozsah 0–1024.
    

---

### Ukázkový kód – servo

```python
from microbit import *
from easymb import motor

# Nastavení serva do středu (přibližně 90°)
motor.servo.driveServo(pin0, 512)

sleep(1000)

# Otočení úplně doprava
motor.servo.driveServo(pin0, 1024)
```

---

## Třída `motor.car`

Třída `car` umožňuje ovládat pohyb auta pomocí tří motorů (vlevo, vpravo, vzadu).

### Konstruktor

```python
car = motor.car(leftPin=pin0, rightPin=pin1, backPin=pin2)
```

- `leftPin` – pin ovládající levý motor (výchozí `pin0`)
    
- `rightPin` – pin ovládající pravý motor (výchozí `pin1`)
    
- `backPin` – pin ovládající zpětný pohon (výchozí `pin2`)
    

---

### `drive(leftPin, rightPin, backPin, motor, value)`

Spustí daný motor s danou intenzitou.

```python
motor.car.drive(pin0, pin1, pin2, "l", 500)
```

#### Parametry

- `leftPin`, `rightPin`, `backPin` – piny připojené k jednotlivým motorům
    
- `motor` – řetězec `"l"` (levý), `"r"` (pravý), `"b"` (zadní)
    
- `value` – hodnota PWM (0–1023)
    

#### Návratová hodnota

- `True` při úspěchu
    

#### Výjimky

- `ValueError` – pokud je zadaný neplatný název motoru
    

---

### `stop()`

Zastaví všechny motory.

```python
car.stop()
```

---

### `forward(time, speed)`

Spustí všechny tři motory na danou dobu a rychlost.

```python
car.forward(time=1000, speed=600)
```

#### Parametry

- `time` – doba běhu v milisekundách
    
- `speed` – PWM hodnota (0–1023)
    

---

### Ukázkový kód – auto

```python
from microbit import *
from easymb import motor

# Inicializace auta
car = motor.car(pin0, pin1, pin2)

# Jízda dopředu na 1 sekundu
car.forward(time=1000, speed=800)

# Zastavení
car.stop()
```

🛈 **Poznámka:** Motory musí být správně připojené a napájené. Pokud se auto nehýbe, ověř propojení a zdroj energie.

[[API reference/Api home\|Api home]]