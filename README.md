# Smart Water Filter System

An IoT-enabled laboratory prototype for TDS-based adaptive routing in household RO+UF+UV water purifiers.

This repository documents a **Technology Readiness Level 4 (TRL-4)** project: the system has been assembled and validated in a laboratory bench setup, but it has not been proven in residential field deployment or production use.

## Overview

The Smart Water Filter System upgrades a conventional household RO+UF+UV purifier with an ESP8266-based sensing and control layer. Instead of routing every litre of water through the RO membrane, the prototype measures inlet TDS and selects either the RO path or UF path based on the active threshold.

The project combines:

- Real-time TDS sensing using a DFRobot Gravity TDS-10 sensor
- ESP8266 NodeMCU firmware for filtering, threshold comparison, and relay control
- Dual 12V solenoid-valve routing for RO and UF paths
- Physical mode switching between Safety Mode and Saving Mode
- Firebase and Flutter based monitoring dashboard
- Laboratory validation over a 100-hour trial

## Problem Statement

Conventional household RO purifiers often process all incoming water through RO, even when the water already falls within acceptable TDS limits. This can increase reject-water generation, energy use, and membrane wear.

The source document identifies four main issues:

- Indiscriminate always-RO routing
- RO reject water generation, stated as 3-5 L reject per litre of purified output in the background discussion
- Accelerated membrane degradation and maintenance cost from unnecessary RO operation
- Lack of user-selectable routing control in typical monitoring-only systems

## Key Features

### Implemented in Laboratory Prototype

- ESP8266 NodeMCU based embedded control
- TDS-based routing between RO and UF paths
- Safety Mode threshold: 300 ppm
- Saving Mode threshold: 500 ppm
- Long-press push-button mode switching
- Relay-controlled RO and UF valve actuation
- Multi-stage TDS filtering: 30 ADC samples, median filtering, 5 rounds averaging
- Firebase data transmission from ESP8266
- Flutter mobile dashboard concept and screens documented in the source
- 100-hour laboratory validation across three water samples

### Not Claimed

- No AI or machine learning is used.
- No production deployment is claimed.
- No patent grant is claimed for this project repository.
- No cloud analytics are claimed beyond Firebase and Flutter dashboard functionality.

## System Architecture

The system is organized into six functional layers:

![Figure 6.1 - System architecture block diagram](images/figure-6-1-system-architecture.png)

| Layer | Description |
| --- | --- |
| Sensor Layer | DFRobot Gravity TDS-10 analog probe feeds the ESP8266 ADC through signal conditioning. |
| Processing Layer | ESP8266 NodeMCU executes sampling, filtering, TDS computation, threshold comparison, relay control, and Wi-Fi transmission. |
| Decision Layer | Firmware compares computed TDS against the active 300 ppm or 500 ppm threshold. |
| Actuation Layer | 2-channel relay module drives normally closed 12V RO and UF solenoid valves. |
| User Interface Layer | Push button toggles operating mode; LEDs indicate active mode. |
| Remote Monitoring Layer | ESP8266 sends data to Firebase Realtime Database for display in a Flutter app. |

See [diagrams/system_architecture.md](diagrams/system_architecture.md).

## Working Principle

Incoming water first passes through standard sediment and activated carbon pre-filtration. The TDS sensor measures the conditioned inlet water and sends an analog signal to the ESP8266.

The firmware filters the ADC readings, computes TDS using the manufacturer calibration polynomial, and compares the result against the active user-selected threshold:

- If TDS is above threshold, the RO valve opens and water is routed through the RO path.
- If TDS is at or below threshold, the UF valve opens and water is routed through the UF path.

Only one path is intended to remain active at a time. In the documented purifier concept, water then passes through UV sterilisation before output.

## Hardware Components

Primary components documented in the source:

- ESP8266 NodeMCU v3
- DFRobot Gravity TDS-10 sensor
- 2-channel optocoupler-isolated relay module
- 12V normally closed RO solenoid valve
- 12V normally closed UF solenoid valve
- Green LED for Safety Mode
- Red LED for Saving Mode
- Momentary push button
- 12V 2A regulated power supply
- 330 ohm current-limiting resistors

See [hardware/components.md](hardware/components.md).

## Firmware Algorithm

The firmware uses a two-level statistical filtering process:

1. Acquire 30 raw ADC readings from A0 at 2 ms intervals.
2. Sort the readings using insertion sort.
3. Select the median value for the round.
4. Repeat the process for 5 independent rounds.
5. Average the 5 medians to obtain the final estimate.
6. Convert voltage to TDS using the polynomial:

```text
TDS = (133.42 * V^3 - 255.86 * V^2 + 857.39 * V) * 0.5
```

The source document states fixed 25 deg C reference compensation with `kValue = 1.0`.

See [firmware/tds_filtering_algorithm.md](firmware/tds_filtering_algorithm.md).

## Mobile Dashboard

The documented dashboard follows:

```text
ESP8266 -> Firebase Realtime Database -> Flutter Android/iOS application
```

![Figure 7.6.1 - Home screen dashboard](images/figure-7-6-1-home-safe-water.jpeg)

The source describes Home, Analytics, and Filters screens showing live TDS, active mode, active path, runtime, water saved, energy metrics, TDS trends, and filter health estimates.

See [mobile-dashboard/firebase_architecture.md](mobile-dashboard/firebase_architecture.md).

## Demonstration Video

A prototype demonstration video showing the operation of the Smart Water Filter System is available.

See [docs/DEMONSTRATION_VIDEO.md](docs/DEMONSTRATION_VIDEO.md).

The video demonstrates:

- Hardware prototype
- TDS measurement
- Adaptive routing
- Safety and Saving modes
- Relay actuation
- System operation

## Figures and Tables

The primary document includes diagrams, dashboard screenshots, prototype photographs, and experimental tables. Embedded images from the DOCX are preserved in [images/](images/), and prototype setup photographs are also available in [prototype/](prototype/).

See [docs/FIGURES_AND_TABLES.md](docs/FIGURES_AND_TABLES.md).

## Experimental Validation Summary

Laboratory validation was conducted over 100 operational hours using three water samples:

| Sample | Measured TDS | Trial Hours | Modes Tested |
| --- | ---: | ---: | --- |
| A | 75.4 +/- 1.2 ppm | 40 h | Safety + Saving |
| B | 415.8 +/- 2.1 ppm | 35 h | Safety + Saving |
| C | 719.3 +/- 3.6 ppm | 25 h | Safety + Saving |

Routing validation reported:

- 100% routing accuracy across 120 measurement cycles
- 0 false transitions
- 218-222 ms actuation latency

100-hour energy and conservation summary:

| Metric | Result |
| --- | ---: |
| Total runtime | 100.0 h |
| UF runtime | 57.5 h |
| RO runtime | 42.5 h |
| Energy consumed | 3.946 kWh |
| Energy saved | 3.163 kWh |
| Reject avoided | 10,350 L |
| Savings | 44.5% |

These are laboratory results only and should not be interpreted as field deployment performance.

## Repository Structure

```text
Smart-Water-Filter-System/
|-- README.md
|-- LICENSE
|-- docs/
|-- images/
|-- firmware/
|-- hardware/
|-- mobile-dashboard/
|-- experiments/
|-- diagrams/
|-- prototype/
`-- future-work/
```

## Technology Stack

- Microcontroller: ESP8266 NodeMCU v3
- Sensor: DFRobot Gravity TDS-10
- Actuation: 2-channel relay module and 12V solenoid valves
- Backend: Firebase Realtime Database
- Mobile app: Flutter
- Documentation diagrams: Mermaid

## Limitations

- TDS alone cannot identify contaminants such as arsenic, fluoride, or nitrate.
- The prototype uses fixed 25 deg C temperature compensation.
- Measurements are event-driven rather than continuous.
- The system has not been tested inside a real purifier housing under household water pressure.
- The source describes a breadboard/laboratory prototype, not a production-ready purifier.
- Field validation is required before claims about residential deployment can be made.

## Future Work

- Add pH sensing.
- Add turbidity sensing.
- Add periodic re-measurement every 30-60 minutes.
- Develop an enclosure suitable for purifier integration.
- Explore AI-assisted predictive filter health as future research only, after long-term data collection and validation.
- Conduct pilot residential studies toward TRL-5.

## License

This repository is released under the MIT License. See [LICENSE](LICENSE).
