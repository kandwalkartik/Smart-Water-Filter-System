# Demonstration Video

Platform: Google Drive

Link:

[https://drive.google.com/file/d/1Q_SPMCIp80n4pEmFWH47styx3cLTCZdv/view?pli=1](https://drive.google.com/file/d/1Q_SPMCIp80n4pEmFWH47styx3cLTCZdv/view?pli=1)

## Description

Demonstration of the laboratory prototype of the IoT-enabled Smart Water Filter System using ESP8266 and adaptive dual-path filtration.

## Demonstrated Elements

- Hardware prototype
- TDS measurement
- Adaptive routing
- Safety and Saving modes
- Relay actuation
- System operation

## System Components and Operation

The video demonstrates a TDS-based smart water adaptive routing system that automatically directs water to different filtration paths based on Total Dissolved Solids (TDS) levels.

Documented operation:

- One solenoid valve represents a UF filtration path.
- One solenoid valve represents an RO filtration path.
- For TDS below 300 ppm, the system routes to the UF path.
- For TDS between 300 ppm and 500 ppm, Saving Mode routes to UF, while Safety Mode can route to RO.
- For TDS above 500 ppm, the system routes to the RO path.

## Monitoring and Analytics

The dashboard demonstrates:

- Current TDS values
- Active filter path
- Daily UF and RO usage time
- Water saved by using UF instead of RO where appropriate
- Filter health estimation
- Energy saving analysis

## Scope Note

This is the only demonstration video documented in this repository. The repository's primary technical documentation uses the ESP8266 NodeMCU as the controller, consistent with the primary project document.
