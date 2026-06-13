# Mode Switching

Label: Implemented

```mermaid
stateDiagram-v2
    [*] --> SafetyMode
    SafetyMode: Threshold 300 ppm
    SavingMode: Threshold 500 ppm

    SafetyMode --> SavingMode: 3-second long press
    SavingMode --> SafetyMode: 3-second long press

    SafetyMode --> Confirmation: LED update + 5 blinks
    SavingMode --> Confirmation: LED update + 5 blinks
    Confirmation --> ReMeasure: Trigger fresh TDS cycle
    ReMeasure --> RouteWater: Apply new threshold
```

## Notes

- Safety Mode is indicated by the green LED.
- Saving Mode is indicated by the red LED.
- The source document states that the routing decision is re-evaluated after mode change.
