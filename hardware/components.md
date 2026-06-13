# Hardware Components

This page documents the hardware described in the primary project document. The system is a laboratory prototype, not a production purifier.

## Core Control and Sensing

| Component | Documented Specification | Purpose |
| --- | --- | --- |
| ESP8266 NodeMCU | v3, 80 MHz, 4 MB flash, built-in Wi-Fi | Main controller and Firebase gateway |
| DFRobot Gravity TDS-10 | 0-1000 ppm range, analog output stated as 0-2.3 V | Inlet water TDS sensing |
| Voltage conditioning | Signal clamped for ESP8266 ADC input | Protects ESP8266 A0 input range |

## Actuation

| Component | Documented Specification | Purpose |
| --- | --- | --- |
| 2-channel relay module | 5V coil, 10A contact, optocoupler isolated | Switches RO and UF valves |
| RO valve | 12V DC, normally closed, G1/4 thread | Opens RO path for high-TDS routing |
| UF valve | 12V DC, normally closed, G1/4 thread | Opens UF path for low-TDS routing |

## User Interface

| Component | Documented Specification | Purpose |
| --- | --- | --- |
| Green LED | 5 mm, 20 mA | Safety Mode indicator, 300 ppm |
| Red LED | 5 mm, 20 mA | Saving Mode indicator, 500 ppm |
| Push button | Momentary tactile switch | 3-second long-press mode switching |
| Current-limiting resistors | 330 ohm, quantity 2 | LED protection |

## Power

| Component | Documented Specification | Purpose |
| --- | --- | --- |
| 12V DC supply | 12V 2A regulated adapter | System power rail for valves and support electronics |

## Notes

- The source document describes normally closed solenoid valves.
- The actuation design is intended to keep RO and UF paths mutually exclusive.
- Any real purifier integration would require enclosure, isolation, pressure, and electrical safety validation beyond the documented bench prototype.
