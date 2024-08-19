---
layout: default
title: "Motion Sensor"
parent: "Components"
nav_order: 6
has_children: false
---

<img src="assets/grove-pir.png" alt="Grove Motion Sensor" width="250"/>

# Motion Sensor
<a href="../../glossary/glossary"><img src="../../glossary/assets/input.png" alt="Input" width="72"/></a> <a href="../../glossary/glossary"><img src="../../glossary/assets/digital.png" alt="Digital" width="72"/></a>

Lorem

---

## Basic Usage
```python
# --- Imports
import digitalio
import time
import board

# --- Variables
motion_sensor = digitalio.DigitalInOut(board.GP16)
motion_sensor.direction = digitalio.Direction.INPUT

# --- Functions

# --- Setup

# --- Main loop
while True:
    if motion_sensor.value == True:
        print("A Motion has occured")
    else:
        print("Nothing...")
        
    time.sleep(0.1)
```

