---
layout: default
title: "Idea 2 - Reaction Game"
parent: "Part 2: Get Creative! Building & Prototyping"
---


# Idea 2 - Reaction Game

This is a simple but exciting two-player reaction game. It lets you practice coding basic logic, working with input and output hardware, and competing with a friend—all with minimal setup.

---

## What does the Reaction Game do?

Once the LED turns white, both players need to press their button as quickly as possible. The game detects who pressed their button first, then lights up the LED in red or blue to indicate the winner. After a short pause, the game resets and you can play again.

---

## How to Play

1. Press the reset/start button to begin (or simply reset the board).
2. Wait until the LED lights up white—it will happen after a random delay.
3. As soon as the LED is white, both players compete to press their button as fast as possible.
4. The first player to press their button wins the round. The LED shows either red or blue to signal the winner.
5. Wait a few seconds for the LED to turn off, and the game resets for a new round.

---

## Components for the Base Game

- Microcontroller board (e.g. Raspberry Pi Pico)
- 2 × Buttons (digital input)
- 1 × RGB (NeoPixel) LED (as output)
- Connection cables

---

## Other Components You May Use

You can expand and personalize your game with:
- More LEDs (for visual feedback, winner indication)
- Additional buttons (to support more players)
- Display (OLED) (to show winner, reaction times, highscore, etc.)
- Buzzer or speaker (for sound effects)

Check the [Components](../components.md) page for what’s available.

---

## Basic Setup

1. **Connect the RGB LED** to a suitable output port/pin.
2. **Connect both buttons** to input ports/pins.
3. **Power and connect your board to your computer.**
4. No resistors or extra manual connections are needed beyond plugging things into the right ports.

*___Insert wiring diagram or setup photo here___*

---

## Code

Below is the complete code for a basic reaction game using two digital inputs (buttons) and an RGB LED for output. Use this as a starting point for your own logic and extensions.

```python
##--- Imports
import digitalio
import board
import neopixel
import time
import random

##--- Variables
state_wait = 0
state_start_game = 1
state_wait_button_press = 2
state_red_wins = 3
state_blue_wins = 4
current_state = 0

# Button variables
red_pin = board.GP1
red_button = digitalio.DigitalInOut(red_pin)
red_button.direction = digitalio.Direction.INPUT

blue_pin = board.GP5
blue_button = digitalio.DigitalInOut(blue_pin)
blue_button.direction = digitalio.Direction.INPUT

# For the Chainable LED:
pin_leds = board.GP16
num_leds = 6
leds = neopixel.NeoPixel(pin_leds, num_leds, auto_write=False, pixel_order=neopixel.GRB)

led_off = (0, 0, 0, 0)
led_red = (255, 0, 0, 0)
led_blue = (0, 0, 255, 0)
led_white = (0, 0, 0, 255)

# Timer variables
timer_duration = 0
timer_mark = 0

##--- Functions
def set_led_color(color):
    global leds
    leds.fill(color)
    leds.show()

def set_timer(duration):
    global timer_duration, timer_mark
    timer_duration = duration
    timer_mark = time.monotonic()

def timer_expired():
    global timer_mark, timer_duration
    if time.monotonic() - timer_mark > timer_duration:
        return True
    else:
        return False

##--- Main loop
while True:
    if current_state == state_wait:
        set_led_color(led_off)
        set_timer(random.randint(3, 10))
        print("starting game!")
        current_state = state_start_game

    elif current_state == state_start_game:
        if timer_expired():
            print("timer expired, press your buttons!")
            set_led_color(led_white)
            current_state = state_wait_button_press

    elif current_state == state_wait_button_press:
        if red_button.value:
            print("red won")
            current_state = state_red_wins
        elif blue_button.value:
            print("blue won")
            current_state = state_blue_wins

    elif current_state == state_blue_wins:
        set_led_color(led_blue)
        time.sleep(3)
        current_state = state_wait

    elif current_state == state_red_wins:
        set_led_color(led_red)
        time.sleep(3)
        current_state = state_wait
```

{:.note}
The original source of this reaction game code can be found [here](https://id-studiolab.github.io/Digital-Interfaces/assignments/02-reaction-game/).


---

## Ideas for Extensions & Variations

- Show winner with extra LEDs or on a display
- Display winning reaction time or keep a high score
- Change the rules: e.g. play "Click Race"—see who clicks their button most in 10 seconds
- Add sound effects with a buzzer**
- Add more players (with extra buttons, LEDs)
- Make color challenges or penalties for pressing at the wrong time
- Create a persistent scoreboard

---

**Start by getting the basic game running, then pick and implement one or more of the extensions above, or invent your own twist!**



---

### Need help?


There are several ways for you to get some help with your prototypes:

1. We have trained a custom ChatGPT-Agent for you that will help you with any questions. This is especially helpful regarding your python-code:

    [DTI Workshop Helper](https://chatgpt.com/g/g-6890968826808191b1bccc15d0e6a983-dti-workshop-helper){: .btn}

2. For references on using specific components, jump to the Components section: 

    [Component Overview](../components/){: .btn}

3. Your workshop instructors are of course happy to help. Don't worry: Go ahead and ask your question.

