# Wiring Connections

This page summarizes the wiring concept from the primary document. Exact pin assignments should be verified against the actual firmware and prototype wiring before replication.

## Documented Connections

| Subsystem | Connection |
| --- | --- |
| TDS sensor | Analog signal to ESP8266 ADC pin A0 through voltage conditioning |
| Push button | GPIO D7 for debounced 3-second long-press detection |
| Relay channel 1 | Controls RO solenoid valve |
| Relay channel 2 | Controls UF solenoid valve |
| Green LED | Indicates Safety Mode, 300 ppm |
| Red LED | Indicates Saving Mode, 500 ppm |
| 12V supply | Powers 12V normally closed solenoid valves and system power rail |

## Relay and Valve Logic

- RO valve opens when measured TDS is above the active threshold.
- UF valve opens when measured TDS is at or below the active threshold.
- The design intent is mutually exclusive actuation so that both paths are not open at the same time.

## Safety Notes

- The source describes a laboratory prototype.
- The repository does not claim a certified electrical or plumbing design.
- Use suitable isolation, fusing, common-ground planning, and waterproofing before any practical replication.
