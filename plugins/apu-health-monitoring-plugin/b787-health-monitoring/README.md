---
description: Configuration
---

# B787 Health Monitoring

Fwot properties

| Property Name           | Value                                           |                                                                                                                 |
| ----------------------- | ----------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| ApuType                 | APS3200 or 131-9A or APS5000 (work in progress) | The APU type.                                                                                                   |
| ApuInstalledDate        | YYYY-MM-DD                                      | value used to display  on DB: apu configuration  (fw.a320.hms-db\_fleet\_apu\_current\_config)                  |
| ApuHoursAtInstallation  | number                                          | value used to calculate TSI and display  on DB: apu configuration (fw.a320.hms-db\_fleet\_apu\_current\_config) |
| ApuCyclesAtInstallation | number                                          | value used to calculate CSI and display  on DB: apu configuration (fw.a320.hms-db\_fleet\_apu\_current\_config) |
| ApuHoursSinceRepair     | number                                          | value used to calculate TSR and display  on DB: apu configuration (fw.a320.hms-db\_fleet\_apu\_current\_config) |
| ApuCyclesSinceRepair    | number                                          | value used to calculate CSR and display  on DB: apu configuration (fw.a320.hms-db\_fleet\_apu\_current\_config) |
