# Filter Health Model

Label: Conceptual dashboard model based on documented formulas

```mermaid
flowchart TD
    A["Session Data"] --> B["RO Runtime"]
    A --> C["UF Runtime"]
    A --> D["UV Runtime"]
    A --> E["TDS During Session"]
    A --> F["Water Throughput"]

    B --> G["RO Damage = t * (TDS / 300)^1.5"]
    E --> G
    G --> H["RO Health = 100 - sum(Damage) / 4800 * 100"]

    C --> I["UF Health = 100 - sum(t_UF) / 3500 * 100"]
    D --> J["UV Health = 100 - sum(t_UV) / 8000 * 100"]
    F --> K["Sediment Filter Throughput Tracking"]

    H --> L["Flutter Filter Health Gauges"]
    I --> L
    J --> L
    K --> L
```

## Notes

- The model supports maintenance planning in the dashboard.
- The values are estimates, not certified remaining-life measurements.
