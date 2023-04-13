# Configuration

This plugin is not enabled by default. You can enable it by FWOT (aircraft). Here is the list of properties you need to set in order to make the plugin work

<mark style="color:purple;">**FWOT properties:**</mark>\


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

| Name        | Value                                                                                                                                | Airline                                                                |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------- |
| REVIMA      | <ul><li><em>value in ["email1", "email2"]</em></li><li><em>REVIMA  Fleet Management engineers to be alerted</em></li></ul>           | (_leave empty if you'd like to receive alerts from all your clients.)_ |
| CLIENT\_ENG | <ul><li><em>value in ["email1", "email2"]</em></li><li><em>HMS APU Power Plant engineers to be alerted</em></li></ul>                | <p>AIR</p><p><em>(airline ICAO code)</em></p>                          |
| CLIENT\_MCC | <ul><li><em>value in ["email1", "email2"]</em></li><li><em>HMS APU Maintenance Control Center Engineers to be alerted</em></li></ul> | <p>AIR</p><p><em>(airline ICAO code)</em></p>                          |



You must define the following _**Constants**_ (some are to set predictive/proactive alerts).&#x20;

_NOTE: the following constants could be customised per Airline. Here below are default values for all airlines:_&#x20;

| Constant Name              | Description                                                                                                                                                                    | Value | APU type:     |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----- | ------------- |
| HMS\_LIMIT\_P\_ALERT       | <ul><li>counter</li><li>threshold used to count number of proactive alerts (P_ALERT)</li><li>send alert when this value is reached in defined days</li></ul>                   | 3     | all APU types |
| HMS\_LIMIT\_DAYS\_P\_ALERT | <ul><li>value in DAYS</li><li>threshold used to count proactive alerts in this amount of days</li><li>send alert when the value of P_ALERTs is reached in those days</li></ul> | 10    | all APU types |

Here below, the **constants** to be defined per APU Type:

{% tabs %}
{% tab title="B787 APU" %}
Predictive Alerts that use constants:

| Constant                              | Description                                                                                                                                                                     | Value | Airline         | P\_ALERT                              |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------- | ------------------------------------- |
| HMS\_APS5000\_LIMIT\_EGT21AMB         | <p></p><ul><li>value in degC</li></ul><ul><li>constant used in calculation of predictive alert for High EGT  (HIGH_EGT_C)</li></ul>                                             | 530   | Default for All | HIGH\_EGT\_C                          |
| HMS\_APS5000\_LIMIT\_PEAK\_EGT\_DELTA | threshold used at DB aps5000 cross section (EGTsensor\_anim)                                                                                                                    | 79.5  | Default for All | NA                                    |
| HMS\_APS5000\_LIMIT\_MES\_OIL\_T      | <p></p><ul><li>value in degC</li></ul><ul><li>constant used in calculation of predictive alert for Oil Temp limit curve to monitor oil cooler clogging (P_OIL_T_HIGH)</li></ul> | 10    | Default for All | P\_OIL\_T\_HIGH                       |
| HMS\_APS5000\_THRESHOLD\_REFILL\_OIL  | <p></p><ul><li>value in quarters</li></ul><ul><li>refill threshold used in calculation of predictive alert for oil consumption at REP202</li></ul>                              | 0.5   | Default for All | OIL\_CONS\_UNSATIS (OIL\_CONSUMPTION) |
| HMS\_APS5000\_LIMIT\_OIL\_DP          | <p></p><p></p><ul><li>value in psid</li></ul><ul><li>limit for Main Oil delta pressure used in calculation of predictive alert for oil delta pressure at REP202</li></ul>       | 40    | Default for All | P\_OIL\_DP                            |
| HMS\_APS5000\_LIMIT\_GEN\_OIL\_DP     | threshold used at DB aps5000 cross section (GenDP\_anim)                                                                                                                        | 20    | Default for All | NA                                    |
| HMS\_APS5000\_LIMIT\_MES\_WFCALC      | <p></p><ul><li>value in pph</li></ul><ul><li>constant used in calculation of predictive alert for MES_WFCALC_LIMIT (Fuel Flow limit in MES)</li></ul>                           | 10    | Default for All | MES\_WFCALC\_HIGH                     |
| HMS\_APS5000\_LIMIT\_TIME\_RTL        | <p></p><ul><li>value in seconds</li></ul><ul><li>time ready to load threshold used in calculation of predictive alert for time ready to load at REP202</li></ul>                | 50    | Default for All | TIME\_RTL\_LIMIT                      |
| HMS\_APS5000\_LIMIT\_DOOR\_CL\_TIME   | <p></p><p></p><ul><li>value in seconds</li></ul><ul><li>Door Closing Time limit is used in calculation of predictive alert for DOOR_CL_TIME at REP202</li></ul>                 | 34    | Default for All | DOOR\_CL\_TIME\_ALERT                 |
| HMS\_APS5000\_LIMIT\_REP202\_NO\_DATA | <p></p><ul><li>value in DAYS</li></ul><ul><li>threshold used at layout OOOI-off</li><li>send indication that APU is not sending data.</li></ul>                                 | 2     | Default for All | NA                                    |
{% endtab %}

{% tab title="A320 APU" %}
Constants used to create Proactive/Predictive Alerts:

| Constant                                   | APU Type       | Description                                                                                                                              | Value  | Airline         | P\_ALERT                                             |
| ------------------------------------------ | -------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ------ | --------------- | ---------------------------------------------------- |
| HMS\_131\_9A\_LIMIT\_MES\_DELTA\_OTA\_LCIT | 131-9A         | <p></p><ul><li>value in degC</li></ul><ul><li>constant used in calculation of predictive alert for Oil Temperature</li></ul>             | 0.9    | Default for All | OIL\_COOLER\_TEMP                                    |
| HMS\_APS3200\_LIMIT\_MES\_DELTA\_OTA\_LCIT | APS3200        | <p></p><ul><li>value in degC</li></ul><ul><li>constant used in calculation of predictive alert for Oil Temperature</li></ul>             | 10     | Default for All | OIL\_COOLER\_TEMP                                    |
| HMS\_A320\_C\_MES\_PT\_CORR                | 131-9A APS3200 | <p></p><ul><li>value in bar</li></ul><ul><li>constant used in calculation of predictive alert for MES Corrected Bleed Pressure</li></ul> | 0.6894 | Default for All | P\_PT\_CORR\_LOW                                     |
| HMS\_A320\_C\_LIMIT\_MES\_EGTA             | 131-9A APS3200 | <p></p><ul><li>value in degC</li></ul><ul><li>constant used in calculation of predictive alert for MES Exhaust Gas Temperature</li></ul> | 10     | Default for All | P\_EGT\_IGV P\_EGT\_BLEED P\_EGT\_RUN STA\_EGT\_HIGH |
| HMS\_A320\_LIMIT\_PREV\_START\_STA         | 131-9A APS3200 | <p></p><ul><li>value in seconds</li></ul><ul><li>used in calculation of predictive alert for Starting Time</li></ul>                     | 55     | Default for All | PREV\_START\_STA\_LIMIT                              |
| HMS\_A320\_LIMIT\_HIGH\_PREV\_START\_NPA   | 131-9A APS3200 | <p></p><ul><li>value in RPM</li></ul><ul><li>used in calculation of predictive alert for Starting Shaft Speed</li></ul>                  | 55     | Default for All | PREV\_START\_NPA\_LIMIT                              |
| HMS\_A320\_LIMIT\_LOW\_PREV\_START\_NPA    | 131-9A APS3200 | <p></p><ul><li>value in RPM</li></ul><ul><li>used in calculation of predictive alert for Starting Shaft Speed</li></ul>                  | 25     | Default for All | PREV\_START\_NPA\_LIMIT                              |
{% endtab %}
{% endtabs %}



You must also add the following _**Documents**_:

| Name                                     | Description                                                                       | data format |
| ---------------------------------------- | --------------------------------------------------------------------------------- | ----------- |
| **FW\_HMS\_APU\_ALERT\_EMAIL\_TEMPLATE** | email template that is used to send alert about any anomaly (predictive or other) | html        |

Here below, the _**Documents**_ to be defined per APU Type:

{% tabs %}
{% tab title="B787 APU" %}
| Name                                    | Description                                                                                                                 | Data Format |
| --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ----------- |
| FW\_HMS\_B787\_MAINTWD\_DECODING        | correlation table between MAINTWDs, Maintenance Messages Code and Description, FIM task and to list of emails for alerting. | csv         |
| FW\_HMS\_B787\_MODEL\_EGT               | predictive model for the APS5000 EGT                                                                                        | python      |
| FW\_HMS\_B787\_MAINTWD\_EMAIL\_TEMPLATE | email template that is used to send alert about any ATA49 maintenance message triggered at CMS report.                      | html        |
| FW\_HMS\_B787\_ANOMALY\_EMAIL\_TEMPLATE | email template that is used to send alert about any anomaly (predictive or other)                                           | html        |
{% endtab %}

{% tab title="A320 APU" %}
| Name                         | Description                                                         | Data Format |
| ---------------------------- | ------------------------------------------------------------------- | ----------- |
| FW\_HMS\_A320\_ASD\_DECODING | correlation table between APU Auto-shutdown Codes and to who alert. | csv         |
| FW\_HMS\_A320\_FAULTCODES    | correlation table between Fault Codes, TSM task and to who alert.   | csv         |
| FW\_HMS\_A320\_ACW\_DECODING | correlation table between APU Control Words for each APU type       | csv         |
{% endtab %}

{% tab title="A380 APU" %}
|                              |                                                                     |     |
| ---------------------------- | ------------------------------------------------------------------- | --- |
| FW\_HMS\_A380\_ASD\_DECODING | correlation table between APU Auto-shutdown Codes and to who alert. | csv |
|                              |                                                                     |     |
|                              |                                                                     |     |
{% endtab %}
{% endtabs %}

Finally, you must set/update the  following _**app config:**_

| Name       | Value |
| ---------- | ----- |
| SEND\_MAIL | true  |
|            |       |
