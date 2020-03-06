# FW.querySamples



You can now query WILCO for samples. It allows to make real analytics on message reception. a new function. Each sample is a [SampleV3IO](https://github.com/flightwatching/wilco-api/blob/master/java/com/fw/wilco/api/SampleV3IO.java)

{% hint style="info" %}
The result will not contain the current sample if you do not specify not from or to
{% endhint %}

```javascript
FW.querySamples(
  regs,           // an array of fwot registrations. if null, this field is replaced by the event's fwot.
  names,          // the name of a parameter or an array of parameter names
  from,           // A date, a moment or a string that specifies the begin time window of the request. can be null
  to,             // A date, a moment or a string that specifies the end time window of the request. if null or not passed, the date of the event is considered
  withInvalid,    // a boolean to mention if WILCO has to return the invalid data. null or no parameter means that it should not
  chronological,  // the ordering of the returned array
  page,           // the paging. 1 by default
  count           // the max count of samples to be returned
)
```

This function is powerful being used asynced

```javascript
const s = await FW.querySamples("ABS", 'A', '2017-05-15T00:00:00');
//returns all the samples of parameter A of fwot ABS since 2017-05-15T00:00:00, up to the event's date
const values = s.map(s=>s.value);
//values is an array of all the values.
```

* 
