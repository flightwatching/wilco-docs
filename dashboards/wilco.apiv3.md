---
description: root of the APIV3 end-point
---

# WILCO.api

WILCO.api allows you to get, post, put, delete... on the server using the APIV3 endpoint. It always return promises and are async.

The credentials are injected according to the person that is logged in

```javascript
#gets all the TECHLOG tagged events between 2 dates
try {
  const events = await WILCO.api.get(`events?tag=TECHLOG&from=${stats.timespan[0]}&to=${stats.timespan[1]}`);
} catch (e){}
```

{% hint style="info" %}
`APIV3` is a field that holds the URL root of the APIV3 end-point. APIV3 has the form: `WILCO.APIV3: "https://<my--deployment>.flightwatching.com/fleet/apiv3/"`
{% endhint %}



