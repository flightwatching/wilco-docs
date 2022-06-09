# Configuration

This plugin is not enabled by default. You can enable it by FWOT (aircraft). Here is the list of properties you need to set in order to make the plugin work

Fwot props:\


| Property name     | Value                                 |                                                                                                                              |
| ----------------- | ------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| FwFuelsaveEnabled | true                                  | If not exactly `true`, then the plugin is not enabled for this FWOT                                                          |
| ApuType           | APS3200 or APS5000 (work in progress) | The APU type. It is used to compute specific consumptions and manage the different APU modes. The exhaustive list is here... |

You must define the following constants:

| Name                                                                                               | Recommanded value | Definition                                                        |
| -------------------------------------------------------------------------------------------------- | ----------------- | ----------------------------------------------------------------- |
| [FUELSAVE\_OVERRUN\_PREDEPARTURE](https://plugins.flightwatching.com/fleet/admin/constants/684775) | 30                | Max APU runtime in predeparture mode before generating an overrun |
| [FUELSAVE\_OVERRUN\_MAINTENANCE](https://plugins.flightwatching.com/fleet/admin/constants/684776)  | 60                | Max APU runtime in maintenance mode before generating an overrun  |
| [FUELSAVE\_OVERRUN\_ARRIVAL](https://plugins.flightwatching.com/fleet/admin/constants/684789)      | 15                | Max APU runtime in arrival mode before generating an overrun      |
| [APU\_FUEL\_TO\_CO2](https://plugins.flightwatching.com/fleet/admin/constants/684790)              | 3.76              | Physic constant, please do not change : Kg of CO2 per Kg of fuel  |
| [APU\_FUEL\_COST](https://plugins.flightwatching.com/fleet/admin/constants/684791)                 | 1.12              | Fuel cost, in $/l                                                 |
| [UPLINKS\_INTERVAL](https://plugins.flightwatching.com/fleet/admin/constants/684792)               | 10                | Please do not modify                                              |
| [FUELSAVE\_DL\_MAIL](https://plugins.flightwatching.com/fleet/admin/constants/726052)              | \[]               | Recipients of overrun alerts                                      |

You must also add the following documents:

| Name                                                                                                 | Definition                                                                                                              |   |
| ---------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | - |
| [FW\_FUELSAVE\_OVERRUN\_EMAIL\_TEMPLATE](https://plugins.flightwatching.com/fleet/admin/docs/111935) | HTML template for the email that is sent to the FUELSAVE_DL_MAIL recipient (see constants) when an overrun is triggered |   |
| [FW\_FUELSAVE\_APU\_CONSUMPTION](https://plugins.flightwatching.com/fleet/admin/docs/111936)         | Reference document that defines the fuel consumption for each APU and APU mode                                          |   |
|                                                                                                      |                                                                                                                         |   |
