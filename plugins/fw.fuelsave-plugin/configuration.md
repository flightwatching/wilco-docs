# Configuration

This plugin is not enabled by default. You can enable it by FWOT (aircraft). Here is the list of properties you need to set in order to make the plugin work

Fwot props:\


<table><thead><tr><th>Property name</th><th width="150">Value</th><th></th></tr></thead><tbody><tr><td>FwFuelsaveEnabled</td><td>true</td><td>If not exactly <code>true</code>, then the plugin is not enabled for this FWOT</td></tr><tr><td>ApuType</td><td>APS3200 or APS5000 (work in progress)</td><td>The APU type. It is used to compute specific consumptions and manage the different APU modes. The exhaustive list is here...</td></tr></tbody></table>

You must define the following constants:

<table><thead><tr><th width="356.3333333333333">Name</th><th>Recommanded value</th><th>Definition</th></tr></thead><tbody><tr><td>FUELSAVE_OVERRUN_PREDEPARTURE</td><td>30</td><td>Max APU runtime in predeparture mode before generating an overrun</td></tr><tr><td>FUELSAVE_OVERRUN_MAINTENANCE</td><td>60</td><td>Max APU runtime in maintenance mode before generating an overrun</td></tr><tr><td>FUELSAVE_OVERRUN_ARRIVAL</td><td>15</td><td>Max APU runtime in arrival mode before generating an overrun</td></tr><tr><td>APU_FUEL_TO_CO2</td><td>3.76</td><td>Physic constant, please do not change : Kg of CO2 per Kg of fuel</td></tr><tr><td>APU_FUEL_COST</td><td>1.12</td><td>Fuel cost, in $/kg</td></tr><tr><td>UPLINKS_INTERVAL</td><td>10</td><td>Please do not modify</td></tr><tr><td>FUELSAVE_DL_MAIL</td><td>[]</td><td>Recipients of overrun alerts</td></tr></tbody></table>

You must also add the following documents:

<table><thead><tr><th width="409.3333333333333">Name</th><th width="336">Definition</th><th></th></tr></thead><tbody><tr><td>FW_FUELSAVE_OVERRUN_EMAIL_TEMPLATE</td><td>HTML template for the email that is sent to the FUELSAVE_<em>DL_</em>MAIL recipient (see constants) when an overrun is triggered</td><td></td></tr><tr><td>FW_FUELSAVE_GENERAL_EMAIL_TEMPLATE</td><td>new HTML template for the email that is sent to the FUELSAVE_<em>DLMAIL recipient (see constants) when an overrun is triggered/DUAL_USE/Battery monitoring.</em></td><td></td></tr><tr><td>FW_FUELSAVE_APU_CONSUMPTION</td><td>Reference document that defines the fuel consumption for each APU and APU mode</td><td></td></tr><tr><td></td><td></td><td></td></tr></tbody></table>

Finally, you must set/update the two following app config:

| Name       | Value |
| ---------- | ----- |
| DO\_UPLINK | true  |
| SEND\_MAIL | true  |
|            |       |
