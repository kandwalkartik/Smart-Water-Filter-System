# Adaptive Threshold Logic

The prototype supports two user-selectable routing thresholds.

| Mode | Threshold | Indicator | Intended Use |
| --- | ---: | --- | --- |
| Safety Mode | 300 ppm | Green LED | Stricter routing for higher water-quality caution |
| Saving Mode | 500 ppm | Red LED | More UF routing when source water is acceptable |

## Routing Decision

```text
if measured_tds > active_threshold:
    route_to_ro()
else:
    route_to_uf()
```

## Mode Switching

The source document describes:

- A firmware boolean variable controlling active mode
- Debounced 3-second long-press detection on GPIO D7
- Immediate mode toggle after long press
- LED state update
- 5-blink confirmation sequence
- Fresh TDS measurement cycle after mode change

## Boundary Meaning

The document describes RO routing when TDS exceeds the active threshold and UF routing when TDS is within acceptable limits. This repository therefore represents `<= threshold` as UF and `> threshold` as RO.
