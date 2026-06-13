# Relay Control

The actuation layer uses a 2-channel relay module to control two normally closed 12V solenoid valves.

## Channels

| Relay Channel | Controlled Device | Routing Condition |
| --- | --- | --- |
| Relay 1 | RO valve | TDS above active threshold |
| Relay 2 | UF valve | TDS at or below active threshold |

## Mutual Exclusion

The source document states that only one purification path should remain active at a time. Firmware should therefore apply a safe switching sequence:

1. Deactivate both relay outputs.
2. Apply a short settling interval if required by hardware.
3. Activate only the selected path relay.
4. Publish the selected path to Firebase.

## Implemented Scope

The repository documents the relay logic described in the primary source. It does not include certified fail-safe hardware design or production electrical validation.
