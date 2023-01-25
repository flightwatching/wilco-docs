# Configuration

This plugin is not enabled by default. You can enable it by FWOT (aircraft). Here is the list of properties you need to set in order to make the plugin work

Fwot props:\


| Property Name           | Value                                           |                                                                                                            |
| ----------------------- | ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| family                  | A320                                            | aircraft family                                                                                            |
| ApuType                 | APS3200 or 131-9A or APS5000 (work in progress) | The APU type.                                                                                              |
| ApuInstalledDate        | YYYY-MM-DD                                      | value used to display  on DB: apu configuration  (fw.hms-db\_fleet\_apu\_current\_config)                  |
| ApuHoursAtInstallation  | number                                          | value used to calculate TSI and display  on DB: apu configuration (fw.hms-db\_fleet\_apu\_current\_config) |
| ApuCyclesAtInstallation | number                                          | value used to calculate CSI and display  on DB: apu configuration (fw.hms-db\_fleet\_apu\_current\_config) |
| ApuHoursSinceRepair     | number                                          | value used to calculate TSR and display  on DB: apu configuration (fw.hms-db\_fleet\_apu\_current\_config) |
| ApuCyclesSinceRepair    | number                                          | value used to calculate CSR and display  on DB: apu configuration (fw.hms-db\_fleet\_apu\_current\_config) |

You must define the following constants:



| Constants Name                        | Description                                                                                                                                                        | Value |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----- |
| HMS\_APS5000\_LIMIT\_OIL\_DP          | <p></p><ul><li>value in psid</li></ul><ul><li>limit for Main Oil delta pressure used in calculation of predictive alert for oil delta pressure at REP202</li></ul> | 40    |
| HMS\_APS5000\_LIMIT\_GEN\_OIL\_DP     | <ul><li>threshold used at DB aps5000 cross section (GenDP_anim)</li></ul>                                                                                          | 20    |
| HMS\_APS5000\_LIMIT\_PEAK\_EGT\_DELTA | <ul><li>threshold used at DB aps5000 cross section (EGTsensor_anim)</li></ul>                                                                                      | 79.5  |
| HMS\_APS5000\_LIMIT\_REP202\_NO\_DATA | <ul><li>value in DAYS</li></ul><ul><li>threshold used at layout OOOI-off</li><li>send indication that APU is not sending data.</li></ul>                           | 2     |
| HMS\_APS5000\_THRESHOLD\_REFILL\_OIL  | <ul><li>value in quarters</li><li>refill threshold used in calculation of predictive alert for oil consumption at REP202</li></ul>                                 | 0.5   |
| HMS\_APS5000\_LIMIT\_TIME\_RTL        | <ul><li>value in seconds</li><li>time ready to load threshold used in calculation of predictive alert for time ready to load at REP202</li></ul>                   | 50    |
| HMS\_APS5000\_LIMIT\_DOOR\_CL\_TIME   | <p></p><ul><li>value in seconds</li></ul><ul><li>Door Closing Time limit is used in calculation of predictive alert for DOOR_CL_TIME at REP202</li></ul>           | 34    |
| ADMIN                                 | <ul><li>value in ["email1"]</li></ul>                                                                                                                              |       |
| REVIMA                                | <ul><li>value in ["email1", "email2"]</li></ul>                                                                                                                    |       |
| CLIENT\_ENG                           | <ul><li>value in ["email1", "email2"]</li><li>HMS APU Power Plant engineers to be alerted</li></ul>                                                                |       |
| CLIENT\_MCC                           | <ul><li>value in ["email1", "email2"]</li><li>HMS APU Maintenance Control Center Engineers to be alerted</li></ul>                                                 |       |

You must also add the following documents:



| Name                                    | Description                                                                                                            | data format |
| --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ----------- |
| FW\_HMS\_B787\_MAINTWD\_DECODING        | correlation table between MAINTWDs, Maintenance Messages, Maintenance Messages Description, FIM task and to who alert. | csv         |
| FW\_HMS\_B787\_MAINTWD\_EMAIL\_TEMPLATE | email template that is used to send alert about any ATA49 maintenance message triggered at CMS report.                 | html        |
| FW\_HMS\_B787\_ANOMALY\_EMAIL\_TEMPLATE | email template that is used to send alert about any anomaly (predictive or other)                                      | html        |
| FW\_HMS\_A320\_FAULTCODES               | correlation table between Fault Codes, TSM task and to who alert.                                                      | csv         |
|                                         |                                                                                                                        |             |

Finally, you must set/update the two following app config:

| Name       | Value |
| ---------- | ----- |
| SEND\_MAIL | true  |
|            |       |
