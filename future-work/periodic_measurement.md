# Periodic Measurement

Status: Future Work

The current system uses event-driven measurement. The primary document identifies periodic re-measurement every 30-60 minutes as a future improvement.

## Motivation

Event-driven measurement reduces unnecessary sensor excitation, but it may miss a mid-day water-quality shift if the source changes between measurement events.

## Proposed Direction

A future firmware version could trigger a fresh TDS measurement:

- Every 30-60 minutes
- After mode changes
- At system start-up
- On explicit user request

## Repository Honesty

Periodic measurement is not claimed as implemented in the current prototype.
