# TDS Filtering Algorithm

The firmware uses a two-level statistical sampling method to stabilize TDS readings from low-cost analog hardware.

## Implemented Algorithm

1. Read 30 raw ADC samples from ESP8266 A0.
2. Use a 2 ms interval between samples.
3. Sort the 30 readings using insertion sort.
4. Select the median value for that round.
5. Repeat the round 5 times.
6. Average the 5 median values.
7. Convert the stabilized voltage to TDS using the manufacturer calibration polynomial.

## TDS Polynomial

```text
TDS = (133.42 * V^3 - 255.86 * V^2 + 857.39 * V) * 0.5
```

The primary document states temperature compensation at a 25 deg C reference with `kValue = 1.0`.

## Purpose

The median stage rejects impulse noise, including relay-switching noise. The 5-round average reduces residual variation before the routing decision is made.

## Honesty Note

This is a deterministic statistical filtering algorithm. It is not AI, machine learning, or predictive modelling.
