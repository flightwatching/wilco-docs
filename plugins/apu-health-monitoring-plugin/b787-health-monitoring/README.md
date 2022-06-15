---
description: Configuration
---

# B787 Health Monitoring

Fwot properties

| Property Name           | Value                                           |                                                                   |
| ----------------------- | ----------------------------------------------- | ----------------------------------------------------------------- |
| ApuType                 | APS3200 or 131-9A or APS5000 (work in progress) | The APU type.                                                     |
| ApuInstalledDate        | YYYY-MM-DD                                      | value used to display  on DB: apu configuration                   |
| ApuHoursAtInstallation  | number                                          | value used to calculate TSI and display  on DB: apu configuration |
| ApuCyclesAtInstallation | number                                          | value used to calculate CSI and display  on DB: apu configuration |
| ApuHoursSinceRepair     | number                                          | value used to calculate TSR and display  on DB: apu configuration |
| ApuCyclesSinceRepair    | number                                          | value used to calculate CSR and display  on DB: apu configuration |
