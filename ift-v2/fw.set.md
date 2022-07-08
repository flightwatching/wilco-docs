---
description: >-
  FW.set(param, value, timestamp, onlyIfChanged, eventId) or
  FW.set([sampleV3IO])
---

# FW.set

### await FW.set(\[sampleV3IO])

You can batch create a set of samples with a single call, by passing an array of samples. This way, you have a better flexibility on other fields of the sample such as the `timelabel`

The passed samples have to comply with the [SampleV3IO definition](https://app.swaggerhub.com/apis/flightwatching/wilco-api/3.0.0#/SampleV3IO) with some additional parameters to control the way it is inserted:&#x20;

* `onlyIfChanged` is an option that makes it possible to create the sample only when the value has changed compared to the previous value. It is useful when you want to log upfronts or downfronts

{% hint style="info" %}
If you do not specify a msgId, the current event is used.\
\
If you do not pass a date, then the computedDate of the current event is used
{% endhint %}

### await FW.set(param, value, timestamp, onlyIfChanged, eventId)

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
    const d = moment.utc(FW.getEvent().computedDate);
    await FW.set('__SNAPSHOT', 'PREV', moment(d).add(-1, 'seconds'));
    await FW.set('__SNAPSHOT', 'MES1');
    await FW.set('__SNAPSHOT', 'MES2', moment(d).add(1, 'seconds'));
    await FW.set('__SNAPSHOT', 'NOLOAD', moment(d).add(2, 'seconds'));
```
