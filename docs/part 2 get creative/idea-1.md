---
layout: default
title: "Idea 1 - Alarm System"
parent: "Part 2: Get Creative! Building & Prototyping"
---

# Idea 1 – Alarm System

This project guides you through building a simple alarm system. You'll learn to use sensors to detect motion or other changes in the environment and trigger an audio alert—a stepping stone to automated, interactive devices!

---

## What does the Alarm System do?

The basic version of this alarm system uses a motion sensor to monitor for movement. Whenever motion is detected, a loud, repetitive alarm sound is played through a buzzer. After a few moments, the system resets and continues monitoring.

You can customize your alarm system with different sensors, lights, displays, or more sophisticated logic, making it the perfect foundation for creative tinkering.

---

## How to Use

1. Power on your alarm system.
2. The system waits and monitors for motion (or another trigger, depending on your setup).
3. When a movement (or, in later versions, a tilt or rapid light change) is detected, the alarm sounds loudly.
4. After a set time, the system resets and resumes monitoring.

---

## Components for the Base System

- Microcontroller board (e.g. Raspberry Pi Pico)
- Motion sensor (e.g. PIR sensor)
- Buzzer or speaker
- Connection cables

---

## Other Components You May Use

You can personalize or extend your alarm system with:
- LEDs (visual alarm, status indicators)
- Additional input sensors: 
    - Tilt/IMU sensor (for movement or angle-based triggers)
    - Light sensor (for break-in by sudden shadow/brightness)
    - Sound sensor (for noise triggers)
    - Buttons (alarm off/reset)
- OLED display (for alarm status or logs)
- More buzzers (different sound patterns)

Check the [Components](../components.md) page for available parts.

---

## Basic Setup

1. **Connect the motion sensor** to a digital input pin.
2. **Connect the buzzer** to a digital output pin.
3. **Power and connect your board to your computer.**
4. Other modules: Plug in LEDs, displays, or additional sensors as needed.

*No extra resistors or manual assembly required for most modules. Just use the right ports and cables.*

*___Insert wiring diagram or setup photo here___*

---

## Code

Here is a simple Python example for an alarm system using a motion sensor and buzzer:

```python

# Import necessary libraries to control pins and add time delays
import digitalio
import board
import time

# Setup the PIR motion sensor as an INPUT device (see Glossary: "Input")
pir_pin = board.GP2  # The pin connected to the motion sensor output
pir_sensor = digitalio.DigitalInOut(pir_pin)  # Configure pin to read digital signals (Input)
pir_sensor.direction = digitalio.Direction.INPUT  # Set pin mode to INPUT

# Setup the buzzer as an OUTPUT device (see Glossary: "Output")
buzzer_pin = board.GP15  # The pin connected to the buzzer
buzzer = digitalio.DigitalInOut(buzzer_pin)  # Configure pin to send digital signals (Output)
buzzer.direction = digitalio.Direction.OUTPUT  # Set pin mode to OUTPUT

# Main loop - program keeps running this code repeatedly (in a "loop")
while True:
    # Read the INPUT from the PIR sensor
    if pir_sensor.value:  # If motion is detected (sensor output is HIGH/True)
        print("Motion detected! Alarm sounding!")  # Send message to serial output/monitor
        # Turn buzzer ON and OFF rapidly to create a beeping alarm for 5 seconds
        for _ in range(50):  # Repeat beep pattern 50 times (~5 seconds)
            buzzer.value = True   # Turn buzzer ON (OUTPUT is HIGH)
            time.sleep(0.05)      # Wait 50 milliseconds
            buzzer.value = False  # Turn buzzer OFF (OUTPUT is LOW)
            time.sleep(0.05)      # Wait another 50 milliseconds
        print("Alarm reset. Monitoring resumed.")  # Show that the alarm has ended
        time.sleep(1)  # Wait 1 second before checking the sensor again (avoids retriggering)
    else:
        buzzer.value = False  # Make sure buzzer is always OFF if there's no motion
        time.sleep(0.1)  # Short delay before next check (loop repeats)


```

---

## Ideas for Extensions & Variations

- **Visual Alarms:**  
  Add an LED (or multi-color LED) that flashes when an alarm is triggered or displays system status (e.g., armed/disarmed).

- **Display Status:**  
  Show alarm status and event log on an OLED screen—include time of last trigger.

- **Sensor Choice:**  
  Use other input devices:
    - A tilt or IMU sensor as an anti-theft/tilt alarm.
    - Use a light sensor to detect sudden changes in illumination (e.g., a door or box opened).
    - Add a sound sensor to trigger if noise is detected.

- **Disarm Mechanism:**  
  Integrate a button or secret sequence to temporarily disable or reset the alarm.

- **Smart Patterns:**  
  Vary the alarm sound pattern based on which sensor triggered the alarm (continuous for motion, beeping sequence for tilt, etc).

- **Silent Mode:**  
  Instead of a buzzer, activate a visual alert or send a message (to a display or over serial).

- **"Trap" Mode:**  
  Add a timer before activation so you can leave the room before the system arms itself.

- **Multi-Zone System:**  
  Monitor several sensors (motion, tilt, and light) and display on the OLED which "zone" was triggered.

- **Event Logging:**  
  Keep track of alarm events and display a list (time, type, how often).

---

**Start by building the basic alarm, then add features to meet your own needs or to solve new problems!**


---

## Need Help?

There are several ways for you to get some help with your prototypes:

1. We have trained a custom ChatGPT-Agent for you that will help you with any questions. This is especially helpful reagarding your python-code:

    [DTI Workshop Helper](https://chatgpt.com/g/g-6890968826808191b1bccc15d0e6a983-dti-workshop-helper){: .btn}

2. For references on using specific components, jump to the Components section: 

    [Component Overview](../components/){: .btn}

3. Your workshop instructors are of course happy to help. Don't worry: Go ahead and ask your question.