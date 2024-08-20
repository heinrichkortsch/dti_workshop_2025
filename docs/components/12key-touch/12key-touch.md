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

This Capacitive Touch Sensor allows you to transform everyday objects into touch interfaces. When you touch any sufficiently conductive material (such as fruit, foil, or even your own body) connected to its pins, the sensor detects a change in capacitance, which you can use to trigger a response in your code. Below is a short example that prints "Touched" to the Serial Monitor whenever any of the sensor's channels detects a change.

Note that the sensor establishes a "baseline" for capacitance when the microcontroller is powered on. If you make any changes to the connected objects' "neutral" state, you will need to restart the microcontroller for the sensor to recalibrate and function correctly.

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
