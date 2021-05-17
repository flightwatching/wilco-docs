---
description: >-
  FW.getEvents(reg, from, to, withDismissed, withHidden, severities, tags,
  count)
---

# FW.getEvents

requests the database for events filtered according to the parameter passed

* `reg`: the registration of the FWOT. if not passed, would return events for all your fleet
* `from`: the min date to search, moment or _YYYY-MM-DDTHH:mm:ss_ string format
* `to` : the max date to search, moment or _YYYY-MM-DDTHH:mm:ss_ string format
* `withDismissed` : include or not the dismissed events
* `showHidden` : includes or not the hidden events
* `severities`: an array of severities to narrow the search \(OR operator\). Severities are one of `IGNORE, CREW, WARNING, FAULT, ERROR, INFO`. If not passed or null, takes all the severities
* `tags`: a list of tags to search for \(OR operator\).
* `count`: the max count for the search \(throttled to 5000 elements max\)

The call returns a promise that is catchable with .then\(\). the callback function returns a list of matching events. If an error occurs, the promise is catchable with .catch\(\)

```javascript
var cms=FW.getEvent();

var tailNb = cms.reg;
var toDate = cms.computedDate;
var fromDate = moment.utc(cms.computedDate).add(-2, 'days');

//FW.getEvents(reg, from, to, withDismissed, showHidden, severities, tags, count)
//we search the events where tags are in "2420FJV7", "2420FJV8" in the last 2 days
const events = await FW.getEvents(cms.reg, fromDate, toDate, true, false, null, ["2420FJV7", "2420FJV8" ], 2);
if (events.length>0) { // if we find at least 1 event
  await FW.notify ("bart.simpson@my-company.com",
             "LGB possible distress",
             "APU Chip Det - APU GEN A under-frequency");
}


```

