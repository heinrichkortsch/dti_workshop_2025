---
layout: default
title: "Mono Speaker"
parent: "Components"
nav_order: 10
has_children: false

---

<img src="assets/audio-amp-speaker.png" alt="Speaker Module" width="500"/>

# Audio Amp & Mono Speaker

<a href="../../glossary/glossary"><img src="../../glossary/assets/output.png" alt="Output" width="72"/></a> <a href="../../glossary/glossary"><img src="../../glossary/assets/digital.png" alt="Digital" width="72"/></a>



---

## Background



## Basic Usage



```python
# --- Imports
import board
import audiomp3
import audiopwmio

# --- Variables
audio = audiopwmio.PWMAudioOut(board.GP9)
decoder = audiomp3.MP3Decoder(open("picohello.mp3", "rb"))

# --- Functions

# --- Setup

# --- Main loop
while True:
    audio.play(decoder)
    while audio.playing:
        pass
        
    print("Done playing!")
    
    time.sleep(10)
```



## Advanced Usage

```python
# --- Imports
import board
import audiomp3
import audiopwmio

# --- Variables
audio = audiopwmio.PWMAudioOut(board.GP9)
decoder = audiomp3.MP3Decoder(open("picohello.mp3", "rb"))

# --- Functions

# --- Setup

# --- Main loop
while True:
    audio.play(decoder)
    while audio.playing:
        pass
        
    print("Done playing!")
    
    time.sleep(10)
```
