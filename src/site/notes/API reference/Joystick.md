---
{"dg-publish":true,"permalink":"/api-reference/joystick/"}
---

# `joystick` class

The `joystick` class provides a method to read analog X and Y values from a joystick connected to the micro:bit. It optionally maps the analog values into a 5×5 grid that corresponds with the micro:bit LED display.

## `joystick.joystickGetXY(pinX, pinY, screen)`

Read the X and Y positions from the joystick.

### Parameters

- **`pinX`** – the pin connected to the joystick's X-axis output (for example `pin1`).
    
- **`pinY`** – the pin connected to the joystick's Y-axis output (for example `pin2`).
    
- **`screen`** – a boolean value. If `True`, the joystick values are scaled down to a 5×5 grid (from 0 to 4) suitable for displaying on the micro:bit’s LED matrix. If `False`, the raw analog values (0–1023) are returned.
    

### Returns

A tuple containing the X and Y coordinates:

- `(coordsX, coordsY)`
    
    - If `screen` is `True`: each coordinate is an integer from 0 to 4.
        
    - If `screen` is `False`: each coordinate is an analog value from 0 to 1023.

### Example

<pre> ```python class joystick: def joystickGetXY(pinX, pinY, screen): # divide it to 5×5 range segmentSize = 1024 / 5 # X axis coordsX = pinX.read_analog() if screen: coordsX = int(coordsX / segmentSize) # Y axis coordsY = pinY.read_analog() if screen: coordsY = int(coordsY / segmentSize) return coordsX, coordsY ``` </pre>
```
from microbit import *
from joystick import joystick

while True:
    x, y = joystick.joystickGetXY(pin1, pin2, True)
    display.set_pixel(x, y, 9)
    sleep(100)
    display.clear()

```

<div style="display: flex; justify-content: center; margin-bottom: 20px;">
  <img src="/img/user/Content/Ev_Herald_Hero_Bardrey_Overall.png" alt="Bardrey Overview" style="width: 50%; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.2);">
</div>
