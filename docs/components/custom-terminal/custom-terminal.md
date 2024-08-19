---
layout: default
title: "Custom Screw Terminal"
parent: "Components"
nav_order: 5
has_children: false
---

<img src="assets/custom-terminal.png" alt="Custom Terminal" width="250"/>

# Custom Screw Terminal
<a href="../../glossary/glossary"><img src="../../glossary/assets/input.png" alt="Input" width="72"/></a> <a href="../../glossary/glossary"><img src="../../glossary/assets/analog.png" alt="Analog" width="72"/></a>

Lorem

---

## Basic photo resistor example
```python
# --- Imports
import time
import board
import analogio

# --- Variables
# Initialize analog input connected to photo resistor
photo_resistor = analogio.AnalogIn(board.A1)

# --- Functions

# --- Setup

# --- Main loop
while True:
    val = photo_resistor.value # Read the photo resistor value
    print(val) # Output the value in the serial monitor
    time.sleep(0.05)  # Make the loop run a little bit slower
```
