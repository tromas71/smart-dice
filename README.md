# Smart Dice

![Smart dice render](images/smart-dice(1).JPG)

A 3D-printed dice with electronics inside. It detects which side is facing up and shows the result on your phone. The dice creates its own Wi-Fi network, so no router or internet is needed.

**Status:** prototype

## Why I built it

I wanted a small project that combines electronics, firmware and mechanical design in one device: a board small enough to fit inside a dice, powered by a battery, and a case that I designed and printed myself.

## What I did

- Chose the components and wired the electronics
- Designed the dice enclosure in SolidWorks and 3D printed it
- Wrote the firmware for the ESP32-C3 (reading the sensor, detecting the top side, running the Wi-Fi access point)
- Made the phone interface that displays the result

## How it works

1. The MPU6050 measures acceleration (and rotation) of the dice.
2. The ESP32-C3 reads the sensor over I2C and works out which side points up from the direction of gravity.
3. The ESP32-C3 runs as a **Wi-Fi access point**. The phone connects to it and opens the page that shows the rolled number.

```
MPU6050 --I2C--> ESP32-C3 Super Mini --Wi-Fi AP--> Phone
                      ^
                  Li-ion battery
```

## Hardware

| Part | Purpose |
|------|---------|
| ESP32-C3 Super Mini | Microcontroller with Wi-Fi |
| MPU6050 breakout board | Accelerometer and gyroscope for detecting the top side |
| Small Li-ion battery | Power supply |

Wiring: [add a wiring diagram or table here, e.g. SDA to GPIO x, SCL to GPIO y]

## Mechanical design and 3D printing

The enclosure was modeled in **SolidWorks**. It is designed to hold the board, sensor and battery inside a dice shape.

- STL file for printing: [`cad/print/smart-dice-case.stl`](cad/print/smart-dice-case.stl)
- Material and settings: [e.g. PLA, 0.2 mm layer height, 20 % infill]
- Iterations: [how many versions you printed and what you changed]

![Inside view](images/renders/smart-dice-render-1.jpg)

## How to use

1. Turn the dice on.
2. On your phone, connect to the Wi-Fi network named `[your SSID]` (password: `[password]`).
3. Open `[address, e.g. 192.168.4.1]` in the browser.
4. Roll the dice and read the result on your phone.

## Build and flash the firmware

- Board: ESP32-C3 (Super Mini)
- Tools: [Arduino IDE / PlatformIO / ESP-IDF]
- Libraries: [list libraries, e.g. for the MPU6050]
- Source code is in [`firmware/`](firmware/)

## What I learned

- [Example: how to determine orientation from accelerometer data]
- [Example: how to fit electronics and a battery into a small printed enclosure]
- [Example: a problem you hit and how you solved it]

## Possible improvements

- [Example: battery charging circuit, custom PCB, power-saving sleep mode]

## Repository structure

- `firmware/` code for the ESP32-C3
- `cad/` SolidWorks sources, STEP and STL files
- `images/` renders and photos

## License

[MIT or other license, or "All rights reserved"]
