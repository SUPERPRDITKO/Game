---
{"dg-publish":true,"permalink":"/api-reference/7-segment-display/"}
---

# `segment.Segment` – řízení 4-místného 7-segmentového displeje

Třída `Segment` umožňuje zobrazovat znaky a text na 4-místném segmentovém displeji s čipem **TM1637** pomocí dvou pinů micro:bitu.

> Interně využívá třídu `TM1637`.

## Konstruktor

```python
segment = Segment(clk=pin0, dio=pin1)
```

- `clk` – pin pro hodinový signál (výchozí `pin0`)
    
- `dio` – pin pro datový signál (výchozí `pin1`)
    

#### Vytvoření instance

```python
from segment import segment

displej = segment.Segment(pin0, pin1)
```

---

## Metody

### `display(text)`

Zobrazí zadaný text na displeji (max. 4 znaky).

```python
displej.display("1234")
```

#### Parametry

- `text` – řetězec nebo číslo, které má být zobrazeno (maximálně 4 znaky)
    

Znaky mimo rozsah mapy budou zobrazeny jako prázdné ( ).

---

### `scroll(text, speed=50)`

Posouvá text po displeji zleva doprava.

```python
displej.scroll("HELLO", speed=100)
```

#### Parametry

- `text` – textový řetězec k posouvání
    
- `speed` – rychlost posunu (v milisekundách na krok)
    

---

## Ukázkový kód

```python
from microbit import *
from easymb import segment

displej = segment.Segment(clk=pin0, dio=pin1)

# Zobrazí číslo
displej.display(123)

sleep(2000)

# Posouvání textu
displej.scroll("MICROBIT", speed=100)
```

---

## Podporované znaky

Displej podporuje písmena a číslice:  
`0–9`, `A–Z`, mezera

Znaky jsou interně mapovány na hodnoty segmentů pomocí slovníku `digit_map`.

[[API reference/Api home\|Api home]]