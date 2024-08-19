---
layout: default
title: "Capacitive Touch (12 Key)"
parent: "Components"
nav_order: 7
has_children: false
---

<img src="assets/12key-touch.png" alt="MPR121 Touch Sensor" width="500"/>

# Capacitive Touch Sensor (MPR121)
<a href="../../glossary/glossary"><img src="../../glossary/assets/input.png" alt="Input" width="72"/></a> <a href="../../glossary/glossary"><img src="../../glossary/assets/iic.png" alt="Digital" width="72"/></a>

Lorem https://www.seeedstudio.com/Grove-12-Key-Capacitive-I2C-Touch-Sensor-V2-MPR121.html

---

## Basic Usage
```python
# --- Imports
import time
import board
import busio
import adafruit_mpr121

# --- Declarations
i2c_port = busio.I2C(scl=board.GP9, sda=board.GP8)

# --- Functions

# --- Setup
mpr121 = adafruit_mpr121.MPR121(i2c_port, address=0x5b)

# --- Main loop
while True:
    for i in range(12):
        if mpr121[i].value:
            print('Input {} touched!'.format(i))
```
