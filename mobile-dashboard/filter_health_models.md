# Filter Health Models

The source document describes session-based cumulative degradation models for filter health display.

## RO Membrane

```text
H_RO = 100 - (sum(Damage_i) / 4800) * 100
Damage_i = t_i * (TDS_i / 300)^1.5
```

Documented rated limit: 4,800 damage-units.

## UF Membrane

```text
H_UF = 100 - (sum(t_UF) / 3500) * 100
```

Documented rated limit: approximately 3,000-3,500 h service interval, represented as 3,500 h in the model.

## UV Lamp

```text
H_UV = 100 - (sum(t_UV) / 8000) * 100
```

Documented rated limit: 8,000 h germicidal lifetime.

## Sediment Pre-Filter

The source describes volumetric throughput tracking with a typical 6,000-8,000 L service interval and replacement at 6 months or 6,000 L throughput, whichever comes first.

## Honesty Note

These are estimation models for dashboard maintenance planning, not certified remaining-life measurements.
