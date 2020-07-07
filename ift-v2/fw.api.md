---
description: a generic object that binds the APIV3 endpoint for standard HTTP functions
---

# FW.api

With this object, you can async call any endpoint from [https://app.swaggerhub.com/apis/flightwatching/wilco-api/3.0.0](https://app.swaggerhub.com/apis/flightwatching/wilco-api/3.0.0). Currently, available methods are `get`, `post`, `put` and `delete`

The returned object is a promise of this object: [https://app.swaggerhub.com/apis/flightwatching/wilco-api/3.0.0](https://app.swaggerhub.com/apis/flightwatching/wilco-api/3.0.0) so that you have the status, all the context and of course the payload under `data`. Promises are often used in conjuction with await keyword

{% hint style="info" %}
It is not necessary to pass the credentials because IFT has already the context. So consider calling the API as if it was public
{% endhint %}

## Examples

Get an event from its ID

```javascript
const event = await FW.api.get(`events/${myId}`);
```



