# Firebase Architecture

The documented mobile architecture is:

```text
ESP8266 -> Firebase Realtime Database -> Flutter mobile application
```

## Data Producer

The ESP8266 uses Wi-Fi to transmit runtime data to Firebase. The primary document lists:

- TDS value
- Active mode
- Active purification path
- Filter usage
- Runtime data

## Backend

Firebase Realtime Database is used as the data exchange layer between the embedded controller and the Flutter application.

## Client

The Flutter application consumes Firebase data and presents dashboard screens for monitoring and maintenance planning.

## Scope Boundary

This repository does not claim cloud analytics beyond Firebase data storage/synchronization and Flutter dashboard display.

## Demonstration Reference

The project demonstration video is documented in [docs/DEMONSTRATION_VIDEO.md](../docs/DEMONSTRATION_VIDEO.md). It includes dashboard monitoring and analytics behavior alongside hardware operation.
