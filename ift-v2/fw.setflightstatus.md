---
description: FW.setFlightStatus(flightStatus)
---

# FW.setFlightStatus

shorthand for `FW.updateProperties({status:flightStatus})`

The flightStatus is one of `PWRUP`, `GATEOUT`, `ENGON`, `TAXIOUT`,  `FLYING`, `TAXIIN`, `GATEIN`, `CLOSED`

For some A/C, it can be also the ACARS code for it. For example Boeing has a 2 letter encoding. You can put directly this value, it will be converted to a flightstatus.

