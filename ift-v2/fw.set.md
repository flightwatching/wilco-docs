---
description: FW.set(param, value, timestamp, onlyIfChanged, eventId)
---

# FW.set

creates a sample for the passed parameter. if timestamp is not passed, then the event timestamp is used



* `param` is a string and is the name of the parameter that will be created. If the parametre does not exists, it will be created on the fly
* `value` is the value of the parameter. It can be a number, a string or an object. If the parameter does not exists yet, then it is creates on the fly with the corresponding type
* The `timestamp` has to be in the format: "yyyy-MM-dd'T'HH:mm:ss" or a date or a moment or any ISO9001 format. if timestamp is not passed, then the event timestamp is used
* `onlyIfChanged` is an option that makes it possible to create the sample only when the value has changed compared to the previous value. It is useful when you want to log upfronts or downfronts
* `eventId` is optional. If not set, the sample is added to the current EVT. if the `eventId` is passed, the sample is added to the specified `eventId`

{% hint style="info" %}
Note that if the sample is added to an other `eventId`, then the IFTs of the other event (eventId) will not be evaluated again.
{% endhint %}

```javascript
if (APUBV=="-"||APUBV=='X') {
  await FW.set("LS_APU_NA",0);
} else if(+APUBV==1) {
	await FW.set("LS_APU_NA",100);
}
```
