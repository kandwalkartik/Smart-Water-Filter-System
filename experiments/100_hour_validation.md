# 100-Hour Validation

Laboratory bench validation was conducted over 100 operational hours across three water samples.

## Experimental Setup

| Parameter | Specification |
| --- | --- |
| Microcontroller | ESP8266 NodeMCU v3 at 80 MHz, 4 MB flash |
| TDS sensor | DFRobot Gravity TDS-10, 0-1000 ppm, analog 0-2.3 V output |
| Reference instrument | HANNA HI9813-6 portable TDS/pH/EC/temperature meter |
| Data logging | Flutter + Firebase mobile app; session-level logging |
| Ambient conditions | 25 +/- 1 deg C laboratory |
| Trial duration | 100 operational hours |
| RO power | 60 W |
| RO reject ratio | 3:1 |
| UV lamp power | 11 W |
| UF path power | 5 W |
| UF membrane rated life | 3,500 h |
| RO membrane damage limit | 4,800 damage-units |

## Water Samples

| Sample | Source | Target TDS | Measured TDS | Trial Hours | Modes Tested |
| --- | --- | --- | ---: | ---: | --- |
| A | Vellore municipal drinking water | 70-80 ppm | 75.4 +/- 1.2 ppm | 40 h | Safety + Saving |
| B | Mixed municipal and groundwater supply from residential apartment usage in Vellore | 410-420 ppm | 415.8 +/- 2.1 ppm | 35 h | Safety + Saving |
| C | Borewell groundwater from Vellore urban residential area | 720 ppm | 719.3 +/- 3.6 ppm | 25 h | Safety + Saving |

## Important Interpretation

Sample B is the adaptive-threshold validation case. It routes to RO in Safety Mode because 416 ppm is above 300 ppm, but routes to UF in Saving Mode because it is below 500 ppm.

These results are laboratory validation results only.
