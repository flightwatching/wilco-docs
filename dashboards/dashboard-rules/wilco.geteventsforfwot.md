---
description: >-
  await WILCO.getEventsForFwot(reg, lastCount, lastUnit, toDate, filters,
  callback)
---

# WILCO.getEventsForFwot

Returns the last events for the given FWOT.

`await WILCO.getEventsForFwot("FW-FAN", 3, 'days', '2002-04-03T02:44:00', {tag: 'ATA36'}, function(fwot, events) { console.log(events); })`

* reg: the FWOT reg
* lastCount: the count of time units you want back in time
* lastUnit: the unit for the time count \(years, months, weeks, days, hours, minutes, seconds\)
* toDate: the reference date for the search. If null, it is current date
* filters: a map with filters according to [https://SITE.flightwatching.com/fleet/apiv3\#events](https://site.flightwatching.com/fleet/apiv3#events) \(like tag, sev, showHidden, withDismissed, important...\)
* callback: the function to call when request succedded. the arguments are `callback(reg, eventArray, status)`

eventArray are with the format described here: [https://github.com/flightwatching/wilco-api/blob/master/java/com/fw/wilco/api/EventV3IO.java](https://github.com/flightwatching/wilco-api/blob/master/java/com/fw/wilco/api/EventV3IO.java)

###  ``

