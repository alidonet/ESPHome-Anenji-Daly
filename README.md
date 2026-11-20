# Anenji–Daly ESP Gateway

[![Minimum ESPHome version](https://img.shields.io/badge/dynamic/regex?url=https%3A%2F%2Fraw.githubusercontent.com%2Falidonet%2FESPHome-Anenji-Daly%2Fmain%2FESPHome%2Fesphome.yaml&search=%5E%5B%20%5Ct%5D%2Bmin_version%3A%5B%20%5Ct%5D%2A%5B%22%27%5D%3F%28%5B0-9%5D%2B%5C.%5B0-9%5D%2B%5C.%5B0-9%5D%2B%29%5B%22%27%5D%3F%5B%20%5Ct%5D%2A%28%3F%3A%23%5B%5E%5Cr%5Cn%5D%2A%29%3F%5Cr%3F%24&replace=%241%2B&flags=m&label=ESPHome&color=000000&logo=esphome)](https://esphome.io/)
[![Latest firmware release](https://img.shields.io/github/v/release/alidonet/ESPHome-Anenji-Daly?label=Firmware)](https://github.com/alidonet/ESPHome-Anenji-Daly/releases/latest)
[![Total release downloads](https://img.shields.io/github/downloads/alidonet/ESPHome-Anenji-Daly/total?label=Release%20downloads)](https://github.com/alidonet/ESPHome-Anenji-Daly/releases)

This is a Home Assistant / ESPHome project for monitoring the Anenji 4.2kW inverter via RS485 port and Daly BMS via BT protocol, as single ESP32 controller.

## Install and configure

1. Download the firmware from [GitHub Releases](https://github.com/alidonet/ESPHome-Anenji-Daly/releases).
   The firmware targets the classic ESP32 (`esp32dev`, chip revision 3.1 or newer).
   Use the `.factory.bin` image for the first USB flash with [ESPHome Web](https://web.esphome.io/).
   The older image in `bin/` predates web-based Daly setup.
2. Configure Wi-Fi over USB with Improv Serial, or connect to the **Anenji Daly Setup**
   access point and enter your Wi-Fi credentials in its captive portal.
3. Open the ESP32's address in a browser. In **Daly setup**, click **Find Daly devices**.
   After 12 seconds, match your Daly by name, MAC address, or signal strength in the list
   and choose its number under **Connect to Daly device**.
4. Wait for **Daly setup status** to confirm the saved device. The ESP32 stores the choice
   after receiving telemetry and reconnects on startup. When replacing a BMS, a failed
   connection attempt keeps the previous choice.

The build requires no `secrets.yaml`. Defaults are a 10-second Daly poll interval,
a 30-second inverter poll interval, and an 80-register Daly status request. If your
BMS does not respond to the extended request, choose **62 registers** in **Daly
telemetry mode** and retry.


Required:
  - ESP32
  - RS485 to TTL converter (good to have a board with TX/RX leds);
  - RJ45 half-cable or connector



This is the simple schematics:
```
┌───────────┐              ┌────────────────┐           ┌────────────────────┐
│           │              │             GND│<--------->│GND           ESP32 │
│       1 B-│<-----B- ---->│B-   RS485   RXD│<--------->│RX2 GPIO17          │
│ RJ45  2 A+│<---- A+ ---->│A+   to TTL  TXD│<--------->│TX2 GPIO16          │
│       8   │<--- GND ---->│GND  module  VCC│<--------->│3.3V             VCC│<--5V
│           │              │                │           │                 GND│<--GND
└───────────┘              └────────────────┘           └────────────────────┘
```

## License and credits

This project is licensed under the [Apache License, Version 2.0](LICENSE).
The ESPHome inverter configuration is adapted from [syssi/esphome-smg-ii](https://github.com/syssi/esphome-smg-ii),
and Daly support uses [syssi/esphome-daly-bms](https://github.com/syssi/esphome-daly-bms).
Both upstream projects are distributed under Apache-2.0.

## Trademarks

Anenji, DALY, ESPHome, Home Assistant, Bluetooth, and other names and marks
belong to their respective owners. They are used to identify products,
technologies, and compatibility.

This project provides unofficial ESP32 firmware for use with Anenji inverters
and DALY BMS units. It is developed independently of the manufacturers.
