# Maintenance Alerts

The Flutter dashboard includes maintenance information based on filter health estimates.

## Filters Screen

The primary document describes:

- RO membrane health gauge
- UF membrane health gauge
- UV lamp health
- Sediment filter health
- Maintenance notes
- Service planning alerts

## Example From Source

The source includes an example Filters screen state:

| Component | Displayed State |
| --- | --- |
| UF health | 98%, Good |
| RO health | 97%, Good |
| UF next clean | No issue detected |
| RO replacement | No service required |

## Scope Boundary

Alerts are dashboard guidance based on runtime and degradation models. They are not a substitute for manufacturer service instructions or water-quality testing.
