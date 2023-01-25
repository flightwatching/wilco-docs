# Configuration

This plugin is not enabled by default. You can enable it by FWOT (aircraft). Here is the list of properties you need to set in order to make the plugin work

<mark style="color:purple;">**FWOT properties:**</mark>\ <mark style="color:purple;">****</mark>

| Property Name                           | Value                                  |                                                                                                    |
| --------------------------------------- | -------------------------------------- | -------------------------------------------------------------------------------------------------- |
| <mark style="color:red;">ApuType</mark> | APS3200,  131-9A , APS5000, PW980, etc | The APU type. <mark style="color:red;">REQUIRED</mark> for the correct functioning of dashboards.  |
| family                                  | A320                                   | only for A320 aircraft family                                                                      |
| ApuInstalledDate                        | YYYY-MM-DD                             | value used to display  on apu configuration dashboard                                              |
| ApuHoursAtInstallation                  | number                                 | value used to calculate TSI and display  on apu configuration dashboard                            |
| ApuCyclesAtInstallation                 | number                                 | value used to calculate CSI and display  on apu configuration dashboard                            |
| ApuHoursSinceRepair                     | number                                 | value used to calculate TSR and display  on apu configuration dashboard                            |
| ApuCyclesSinceRepair                    | number                                 | value used to calculate CSR and display  on apu configuration dashboard                            |



You must define the following _**Constants**_ to set the ALERTs notification:

| Name                                 | Value                                                                                                                                | Airline                                                              |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------- |
| REVIMA                               | \["fleetmanagement@revima.com"]                                                                                                      |                                                                      |
| _(do not change that constant name)_ | _value in \["email1", "email2"]_                                                                                                     | _leave empty if you'd like to receive alerts from all your clients._ |
| CLIENT\_ENG                          | \["mail1@airline.com", "mail2@airline.com" ]                                                                                         | AIR                                                                  |
| _(do not change that constant name)_ | <ul><li><em>value in ["email1", "email2"]</em></li><li><em>HMS APU Power Plant engineers to be alerted</em></li></ul>                | _(airline ICAO code)_                                                |
| CLIENT\_MCC                          | \["mail1@airlineMCC.com", "mail2@airlineMCC.com" ]                                                                                   | AIR                                                                  |
| _(do not change that constant name)_ | <ul><li><em>value in ["email1", "email2"]</em></li><li><em>HMS APU Maintenance Control Center Engineers to be alerted</em></li></ul> | _(airline ICAO code)_                                                |



You must define the following _**Constants**_ to set predictive/proactive alerts:

| Constants Name                           | Description                                                                                                                                                                    | Value  | APU type:       |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------ | --------------- |
| HMS\_LIMIT\_P\_ALERT                     | <ul><li>counter</li><li>threshold used to count number of proactive alerts (P_ALERT)</li><li>send alert when this value is reached in defined days</li></ul>                   | 3      | all APU types   |
| HMS\_LIMIT\_DAYS\_P\_ALERT               | <ul><li>value in DAYS</li><li>threshold used to count proactive alerts in this amount of days</li><li>send alert when the value of P_ALERTs is reached in those days</li></ul> | 10     | all APU types   |
| HMS\_APS5000\_LIMIT\_OIL\_DP             | <p></p><ul><li>value in psid</li></ul><ul><li>limit for Main Oil delta pressure used in calculation of predictive alert for oil delta pressure at REP202</li></ul>             | 40     | APS5000         |
| HMS\_APS5000\_LIMIT\_GEN\_OIL\_DP        | <ul><li>threshold used at DB aps5000 cross section (GenDP_anim)</li></ul>                                                                                                      | 20     | APS5000         |
| HMS\_APS5000\_LIMIT\_PEAK\_EGT\_DELTA    | <ul><li>threshold used at DB aps5000 cross section (EGTsensor_anim)</li></ul>                                                                                                  | 79.5   | APS5000         |
| HMS\_APS5000\_LIMIT\_REP202\_NO\_DATA    | <ul><li>value in DAYS</li></ul><ul><li>threshold used at layout OOOI-off</li><li>send indication that APU is not sending data.</li></ul>                                       | 2      | APS5000         |
| HMS\_APS5000\_THRESHOLD\_REFILL\_OIL     | <ul><li>value in quarters</li><li>refill threshold used in calculation of predictive alert for oil consumption at REP202</li></ul>                                             | 0.5    | APS5000         |
| HMS\_APS5000\_LIMIT\_TIME\_RTL           | <ul><li>value in seconds</li><li>time ready to load threshold used in calculation of predictive alert for time ready to load at REP202</li></ul>                               | 50     | APS5000         |
| HMS\_APS5000\_LIMIT\_DOOR\_CL\_TIME      | <p></p><ul><li>value in seconds</li></ul><ul><li>Door Closing Time limit is used in calculation of predictive alert for DOOR_CL_TIME at REP202</li></ul>                       | 34     | APS5000         |
| HMS\_APS5000\_LIMIT\_MES\_WFCALC         | <ul><li>value in pph</li><li>constant used in calculation of predictive alert for MES_WFCALC_LIMIT (Fuel Flow limit in MES)</li></ul>                                          | 10     | APS5000         |
| HMS\_APS5000\_LIMIT\_MES\_OIL\_T         | <ul><li>value in degC</li><li>constant used in calculation of predictive alert for Oil Temp limit curve to monitor oil cooler clogging (P_OIL_T_HIGH)</li></ul>                | 10     | APS5000         |
| HMS\_A320\_LIMIT\_PREV\_START\_STA       | <ul><li>value in seconds</li><li>used in calculation of predictive alert for Starting Time</li></ul>                                                                           | 55     | APS3200, 131-9A |
| HMS\_A320\_LIMIT\_HIGH\_PREV\_START\_NPA | <ul><li>value in RPM</li><li>used in calculation of predictive alert for Starting Shaft Speed</li></ul>                                                                        | 55     | APS3200, 131-9A |
| HMS\_A320\_LIMIT\_LOW\_PREV\_START\_NPA  | <ul><li>value in RPM</li><li>used in calculation of predictive alert for Starting Shaft Speed</li></ul>                                                                        | 25     | APS3200, 131-9A |
| HMS\_A320\_C-LIMIT\_MES\_EGTA            | <ul><li>value in degC</li><li>constant used in calculation of predictive alert for MES Exhaust Gas Temperature</li></ul>                                                       | 10     | APS3200, 131-9A |
| HMS\_A320\_C\_MES\_PT\_CORR              | <ul><li>value in degC</li><li>constant used in calculation of predictive alert for MES Corrected Bleed Pressure</li></ul>                                                      | 0.6894 | APS3200, 131-9A |

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
