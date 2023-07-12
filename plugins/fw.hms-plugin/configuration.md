# Configuration

This plugin is not enabled by default. You can enable it by FWOT (aircraft). Here is the list of properties you need to set in order to make the plugin work

<mark style="color:purple;">**FWOT properties:**</mark>\


| Property Name                           | Value                                  |                                                                                                    |
| --------------------------------------- | -------------------------------------- | -------------------------------------------------------------------------------------------------- |
| <mark style="color:red;">ApuType</mark> | APS3200,  131-9A , APS5000, PW980, etc | The APU type. <mark style="color:red;">REQUIRED</mark> for the correct functioning of dashboards.  |
| family                                  | A320                                   | only for A320 aircraft family                                                                      |
| APU\_INSTALLATION\_DATE                 | YYYY-MM-DD                             | value used to display  on apu configuration dashboard                                              |
| apu\_hrs\_at\_installation              | number                                 | value used to calculate TSI and display  on apu configuration dashboard                            |
| apu\_cyc\_at\_installation              | number                                 | value used to calculate CSI and display  on apu configuration dashboard                            |



You must define the following _**Constants**_ to set the ALERTs notification:

| Name        | Value                                                                                                                                | Airline                                                                |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------- |
| REVIMA      | <ul><li><em>value in ["email1", "email2"]</em></li><li><em>REVIMA  Fleet Management engineers to be alerted</em></li></ul>           | (_leave empty if you'd like to receive alerts from all your clients.)_ |
| CLIENT\_ENG | <ul><li><em>value in ["email1", "email2"]</em></li><li><em>HMS APU Power Plant engineers to be alerted</em></li></ul>                | <p>AIR</p><p><em>(airline ICAO code)</em></p>                          |
| CLIENT\_MCC | <ul><li><em>value in ["email1", "email2"]</em></li><li><em>HMS APU Maintenance Control Center Engineers to be alerted</em></li></ul> | <p>AIR</p><p><em>(airline ICAO code)</em></p>                          |



You must define the following _**Constants**_ (some are to set predictive/proactive alerts).&#x20;

_NOTE: the following constants could be customised per Airline. Here below are default values for all airlines:_&#x20;

<table><thead><tr><th width="368">Constant Name</th><th width="319">Description</th><th width="86">Value</th><th>APU type:</th></tr></thead><tbody><tr><td>HMS_LIMIT_P_ALERT</td><td><ul><li>counter</li><li>threshold used to count number of proactive alerts (P_ALERT)</li><li>send alert when this value is reached in defined days</li></ul></td><td>3</td><td>all APU types</td></tr><tr><td>HMS_LIMIT_DAYS_P_ALERT</td><td><ul><li>value in DAYS</li><li>threshold used to count proactive alerts in this amount of days</li><li>send alert when the value of P_ALERTs is reached in those days</li></ul></td><td>10</td><td>all APU types</td></tr></tbody></table>

Here below, the **constants** to be defined per APU Type:

{% tabs %}
{% tab title="B787 APU" %}
Predictive Alerts that use constants:

<table><thead><tr><th width="311">Constant</th><th width="291">Description</th><th width="79">Value</th><th width="88">Airline</th><th>P_ALERT</th></tr></thead><tbody><tr><td>HMS_APS5000_LIMIT_EGT21AMB</td><td><p></p><ul><li>value in degC</li></ul><ul><li>constant used in calculation of predictive alert for High EGT  (HIGH_EGT_C)</li></ul></td><td>530</td><td>Default for All</td><td>HIGH_EGT_C</td></tr><tr><td>HMS_APS5000_LIMIT_PEAK_EGT_DELTA</td><td>threshold used at DB aps5000 cross section (EGTsensor_anim)</td><td>79.5</td><td>Default for All</td><td>NA</td></tr><tr><td>HMS_APS5000_LIMIT_MES_OIL_T</td><td><p></p><ul><li>value in degC</li></ul><ul><li>constant used in calculation of predictive alert for Oil Temp limit curve to monitor oil cooler clogging (P_OIL_T_HIGH)</li></ul></td><td>10</td><td>Default for All</td><td>P_OIL_T_HIGH</td></tr><tr><td>HMS_APS5000_THRESHOLD_REFILL_OIL</td><td><p></p><ul><li>value in quarters</li></ul><ul><li>refill threshold used in calculation of predictive alert for oil consumption at REP202</li></ul></td><td>0.5</td><td>Default for All</td><td>OIL_CONS_UNSATIS (OIL_CONSUMPTION)</td></tr><tr><td>HMS_APS5000_LIMIT_OIL_DP</td><td><p></p><p></p><ul><li>value in psid</li></ul><ul><li>limit for Main Oil delta pressure used in calculation of predictive alert for oil delta pressure at REP202</li></ul></td><td>40</td><td>Default for All</td><td>P_OIL_DP</td></tr><tr><td>HMS_APS5000_LIMIT_GEN_OIL_DP</td><td>threshold used at DB aps5000 cross section (GenDP_anim)</td><td>20</td><td>Default for All</td><td>NA</td></tr><tr><td>HMS_APS5000_LIMIT_MES_WFCALC</td><td><p></p><ul><li>value in pph</li></ul><ul><li>constant used in calculation of predictive alert for MES_WFCALC_LIMIT (Fuel Flow limit in MES)</li></ul></td><td>10</td><td>Default for All</td><td>MES_WFCALC_HIGH</td></tr><tr><td>HMS_APS5000_LIMIT_TIME_RTL</td><td><p></p><ul><li>value in seconds</li></ul><ul><li>time ready to load threshold used in calculation of predictive alert for time ready to load at REP202</li></ul></td><td>50</td><td>Default for All</td><td>TIME_RTL_LIMIT</td></tr><tr><td>HMS_APS5000_LIMIT_DOOR_CL_TIME</td><td><p></p><p></p><ul><li>value in seconds</li></ul><ul><li>Door Closing Time limit is used in calculation of predictive alert for DOOR_CL_TIME at REP202</li></ul></td><td>34</td><td>Default for All</td><td>DOOR_CL_TIME_ALERT</td></tr><tr><td>HMS_APS5000_LIMIT_REP202_NO_DATA</td><td><p></p><ul><li>value in DAYS</li></ul><ul><li>threshold used at layout OOOI-off</li><li>send indication that APU is not sending data.</li></ul></td><td>2</td><td>Default for All</td><td>NA</td></tr></tbody></table>
{% endtab %}

{% tab title="A320 APU" %}
Constants used to create Proactive/Predictive Alerts:

<table><thead><tr><th width="237">Constant</th><th width="107">APU Type</th><th width="208">Description</th><th>Value</th><th>Airline</th><th>P_ALERT</th></tr></thead><tbody><tr><td>HMS_131_9A_LIMIT_MES_DELTA_OTA_LCIT</td><td>131-9A</td><td><p></p><ul><li>value in degC</li></ul><ul><li>constant used in calculation of predictive alert for Oil Temperature</li></ul></td><td>0.9</td><td>Default for All</td><td>OIL_COOLER_TEMP</td></tr><tr><td>HMS_APS3200_LIMIT_MES_DELTA_OTA_LCIT</td><td>APS3200</td><td><p></p><ul><li>value in degC</li></ul><ul><li>constant used in calculation of predictive alert for Oil Temperature</li></ul></td><td>10</td><td>Default for All</td><td>OIL_COOLER_TEMP</td></tr><tr><td>HMS_A320_C_MES_PT_CORR</td><td>131-9A APS3200</td><td><p></p><ul><li>value in bar</li></ul><ul><li>constant used in calculation of predictive alert for MES Corrected Bleed Pressure</li></ul></td><td>0.6894</td><td>Default for All</td><td>P_PT_CORR_LOW</td></tr><tr><td>HMS_A320_C_LIMIT_MES_EGTA</td><td>131-9A APS3200</td><td><p></p><ul><li>value in degC</li></ul><ul><li>constant used in calculation of predictive alert for MES Exhaust Gas Temperature</li></ul></td><td>10</td><td>Default for All</td><td>P_EGT_IGV P_EGT_BLEED P_EGT_RUN STA_EGT_HIGH</td></tr><tr><td>HMS_A320_LIMIT_PREV_START_STA</td><td>131-9A APS3200</td><td><p></p><ul><li>value in seconds</li></ul><ul><li>used in calculation of predictive alert for Starting Time</li></ul></td><td>55</td><td>Default for All</td><td>PREV_START_STA_LIMIT</td></tr><tr><td>HMS_A320_LIMIT_HIGH_PREV_START_NPA</td><td>131-9A APS3200</td><td><p></p><ul><li>value in RPM</li></ul><ul><li>used in calculation of predictive alert for Starting Shaft Speed</li></ul></td><td>55</td><td>Default for All</td><td>PREV_START_NPA_LIMIT</td></tr><tr><td>HMS_A320_LIMIT_LOW_PREV_START_NPA</td><td>131-9A APS3200</td><td><p></p><ul><li>value in RPM</li></ul><ul><li>used in calculation of predictive alert for Starting Shaft Speed</li></ul></td><td>25</td><td>Default for All</td><td>PREV_START_NPA_LIMIT</td></tr></tbody></table>
{% endtab %}
{% endtabs %}



You must also add the following _**Documents**_:

<table><thead><tr><th width="418">Name</th><th width="241.33333333333331">Description</th><th>data format</th></tr></thead><tbody><tr><td><strong>FW_HMS_APU_ALERT_EMAIL_TEMPLATE</strong></td><td>email template that is used to send alert about any anomaly (predictive or other)</td><td>html</td></tr></tbody></table>

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
