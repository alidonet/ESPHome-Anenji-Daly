This is a Home Assistant / ESPHome project for monitoring the Anenji 4.2kW inverter via RS485 port and Daly BMS via BT protocol, as single ESP32 controller.

Based on the great projects https://github.com/syssi/esphome-smg-ii and https://github.com/syssi/esphome-daly-bms


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