---
description: FW.postEvent(eventV3IO)
---

# FW.postEvent

posts an event. There are help functions to make it easier.

The eventV3IO complies to the definition found [here](https://github.com/flightwatching/wilco-api/blob/master/java/com/fw/wilco/api/EventV3IO.java)

When creating a date, we first check if the string matches known [ISO 8601](https://en.wikipedia.org/wiki/ISO\_8601) formats, we then check if the string matches the [RFC 2822](https://tools.ietf.org/html/rfc2822#section-3.3) Date time format before dropping to the fall back of new Date(string) if a known format is not found.

Example:

```javascript
let event = new EventV3IO("MY_FWOT");
event.addSample("extTemperature", 18) // would crate a parameter if not exists and a sample
event.addSample("extHumidity", 40) // would crate a parameter if not exists and a sample
event.title="Sensor temp="+18;
event.layoutRef = "fw.turnaround-schedule"; // the layout ref
//event.layoutId=4917788; // the ID of the layout associated with the message (if you need it)
event.date = '1973-03-03'; // would set the computedDate
//event.visible=false;
var hour=moment().hours(); // you can use the moment library and the _ library
if (hour>=8&&hour<=19) {
	event.status="flying";
} else {
	event.status="gatein";
}
FW.postEvent(event)
```

### `` ``
