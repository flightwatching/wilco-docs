---
description: >-
  await WILCO.getSamplesForFwot(reg, params, lastCount, lastUnit, toDate,
  callback)
---

# WILCO.getSamplesForFwot

returns the samples in the format: [https://github.com/flightwatching/wilco-api/blob/master/java/com/fw/wilco/api/SampleV3IO.java](https://github.com/flightwatching/wilco-api/blob/master/java/com/fw/wilco/api/SampleV3IO.java)

* reg: the FWOT reg
* params: an array of parameter names (strings)
* lastCount: the count of time units you want back in time
* lastUnit: the unit for the time count (years, months, weeks, days, hours, minutes, seconds)
* toDate: the reference date for the search. If null, it is current date
* callback: the function to call when request succedded. the arguments are `callback(reg, sampleArray, status)`

### `` ``
