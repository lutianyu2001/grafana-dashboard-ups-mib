# Grafana Dashboard: UPS Monitor (RFC 1628 UPS-MIB)

A vendor-neutral Grafana dashboard for monitoring UPS devices via SNMP, based on the IETF RFC 1628 UPS-MIB standard (`1.3.6.1.2.1.33`).

Published on [Grafana dashboards](https://grafana.com/grafana/dashboards) so you can import directly using ID **[25293](https://grafana.com/grafana/dashboards/25293)**.

Tested with *APC Back-UPS ES 600M1* collected via *[NUT](https://github.com/networkupstools/nut)*, bridged to SNMPv3 through *[nut2snmp](https://github.com/lutianyu2001/nut2snmp)*, and scraped by *Prometheus [snmp_exporter](https://github.com/prometheus/snmp_exporter)*. Works like a charm.

## Features

1. **Vendor-neutral**: uses only standard RFC 1628 OIDs, no proprietary MIBs
2. **Dual Voltage Support**: supports both 120V and 220V grid voltage
3. **Auto-detect Grid Voltage**: automatically determines 120V or 220V from input voltage data. You can manually override this by selecting 120V or 220V from the Grid Voltage dropdown at the top of the dashboard. You will also be prompted to set a default fallback voltage when importing the dashboard, in case auto-detection fails.
4. **Voltage Reference Lines**: nominal, +10%, and -10% thresholds on the voltage trend chart
5. **Single & Three-phase Support**: panels adapt to show L1/L2/L3 when available

## Screenshots

|                                                                     Single-phase                                                                      |                                                                     Three-phase                                                                      |
| ----------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![Screenshot of the dashboard in single-phase scenario](https://blog.moeo.org/picx-images-hosting/grafana-dashboard-ups-mib-screenshots/1-phase.webp) | ![Screenshot of the dashboard in three-phase scenario](https://blog.moeo.org/picx-images-hosting/grafana-dashboard-ups-mib-screenshots/3-phase.webp) |

## Metrics Used

|             Metric             |            OID            |                       Description                       |
| ------------------------------ | ------------------------- | ------------------------------------------------------- |
| `upsIdentManufacturer`         | .1.3.6.1.2.1.33.1.1.1     | Manufacturer name                                       |
| `upsIdentModel`                | .1.3.6.1.2.1.33.1.1.2     | Model name                                              |
| `upsIdentUPSSoftwareVersion`   | .1.3.6.1.2.1.33.1.1.4     | Firmware version                                        |
| `upsBatteryStatus`             | .1.3.6.1.2.1.33.1.2.1     | Battery status (1=unknown, 2=normal, 3=low, 4=depleted) |
| `upsEstimatedChargeRemaining`  | .1.3.6.1.2.1.33.1.2.4     | Battery charge %                                        |
| `upsEstimatedMinutesRemaining` | .1.3.6.1.2.1.33.1.2.3     | Estimated runtime in minutes                            |
| `upsBatteryVoltage`            | .1.3.6.1.2.1.33.1.2.5     | Battery voltage (0.1V units)                            |
| `upsBatteryCurrent`            | .1.3.6.1.2.1.33.1.2.6     | Battery current (0.1A units)                            |
| `upsInputVoltage`              | .1.3.6.1.2.1.33.1.3.3.1.3 | Input voltage (per phase)                               |
| `upsOutputSource`              | .1.3.6.1.2.1.33.1.4.1     | Output source (3=normal, 5=battery, etc.)               |
| `upsOutputVoltage`             | .1.3.6.1.2.1.33.1.4.4.1.2 | Output voltage (per phase)                              |
| `upsOutputPercentLoad`         | .1.3.6.1.2.1.33.1.4.4.1.5 | Output load % (per phase)                               |

## License

Copyright 2026 Tianyu (Sky) Lu

The entire repository is licensed under the Apache License, Version 2.0 
(the "License"); you may not use any file in this repository except in 
compliance with the License. You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

## Author

Tianyu (Sky) Lu
