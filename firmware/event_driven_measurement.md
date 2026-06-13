# Event-Driven Measurement

The source document describes event-driven TDS measurement as part of the system design.

## Measurement Events

TDS measurement is triggered on:

- System start-up
- Mode change
- Explicit user demand

After a mode change, a fresh TDS measurement cycle is triggered so the routing state can be re-evaluated under the new threshold.

## Rationale

The document identifies electrode polarisation and electrolytic degradation as concerns in continuous-sensing IoT water-quality systems. Event-driven measurement reduces unnecessary sensor excitation.

## Limitation

Because measurement is not continuous, the system may miss a water-quality change between events. The source document identifies periodic re-measurement every 30-60 minutes as future work.
