# System Architecture

Label: Implemented laboratory prototype with conceptual mobile presentation layer

```mermaid
flowchart LR
    A["Incoming Water"] --> B["Sediment + Activated Carbon Pre-Filters"]
    B --> C["DFRobot Gravity TDS-10 Sensor"]
    C --> D["ESP8266 NodeMCU"]
    D --> E{"TDS > Active Threshold?"}
    E -- "Yes" --> F["Relay 1: RO Valve"]
    E -- "No" --> G["Relay 2: UF Valve"]
    F --> H["RO Path"]
    G --> I["UF Path"]
    H --> J["UV Stage"]
    I --> J
    J --> K["Filtered Output"]
    D --> L["Firebase Realtime Database"]
    L --> M["Flutter Mobile Dashboard"]
    N["Push Button"] --> D
    D --> O["Mode LEDs"]
```

## Notes

- The water-routing controller and relay actuation are documented as implemented in the laboratory prototype.
- The Flutter/Firebase dashboard is documented in the primary source as the monitoring architecture and screen design.
