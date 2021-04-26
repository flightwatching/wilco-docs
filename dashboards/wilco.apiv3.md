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



```javascript
//definition of main calls
const get = await WILCO.api.get(url, options);
const post = await WILCO.api.post(url, data, options)
const put = await WILCO.api.put(url, data, options)
const delete = await WILCO.api.delete(url, data, options)

```

## **Options**

* **params** – `{Object.<string|Object>}` – Map of strings or objects which will be serialized with the `paramSerializer` and appended as GET parameters.
* **headers** – `{Object}` – Map of strings or functions which return strings representing HTTP headers to send to the server. If the return value of a function is null, the header will not be sent. Functions accept a config object as an argument.
* **eventHandlers** - `{Object}` - Event listeners to be bound to the XMLHttpRequest object. To bind events to the XMLHttpRequest upload object, use `uploadEventHandlers`. The handler will be called in the context of a `$apply` block.
* **uploadEventHandlers** - `{Object}` - Event listeners to be bound to the XMLHttpRequest upload object. To bind events to the XMLHttpRequest object, use `eventHandlers`. The handler will be called in the context of a `$apply` block.
* **xsrfHeaderName** – `{string}` – Name of HTTP header to populate with the XSRF token.
* **xsrfCookieName** – `{string}` – Name of cookie containing the XSRF token.
* **transformRequest** – `{function(data, headersGetter)|Array.<function(data, headersGetter)>}` – transform function or an array of such functions. The transform function takes the http request body and headers and returns its transformed \(typically serialized\) version. See [Overriding the Default Transformations](https://docs.angularjs.org/api/ng/service/$http#overriding-the-default-transformations-per-request)
* **transformResponse** – `{function(data, headersGetter, status)|Array.<function(data, headersGetter, status)>}` – transform function or an array of such functions. The transform function takes the http response body, headers and status and returns its transformed \(typically deserialized\) version. See [Overriding the Default Transformations](https://docs.angularjs.org/api/ng/service/$http#overriding-the-default-transformations-per-request)
* **paramSerializer** - `{string|function(Object<string,string>):string}` - A function used to prepare the string representation of request parameters \(specified as an object\). If specified as string, it is interpreted as function registered with the [$injector](https://docs.angularjs.org/api/auto/service/$injector), which means you can create your own serializer by registering it as a [service](https://docs.angularjs.org/api/auto/service/$provide#service). The default serializer is the [$httpParamSerializer](https://docs.angularjs.org/api/ng/service/$httpParamSerializer); alternatively, you can use the [$httpParamSerializerJQLike](https://docs.angularjs.org/api/ng/service/$httpParamSerializerJQLike)
* **cache** – `{boolean|Object}` – A boolean value or object created with [`$cacheFactory`](https://docs.angularjs.org/api/ng/service/$cacheFactory) to enable or disable caching of the HTTP response. See [$http Caching](https://docs.angularjs.org/api/ng/service/$http#caching) for more information.
* **timeout** – `{number|Promise}` – timeout in milliseconds, or [promise](https://docs.angularjs.org/api/ng/service/$q) that should abort the request when resolved.

  A numerical timeout or a promise returned from [$timeout](https://docs.angularjs.org/api/ng/service/$timeout), will set the `xhrStatus` in the [response](https://docs.angularjs.org/api/ng/service/$http#$http-returns) to "timeout", and any other resolved promise will set it to "abort", following standard XMLHttpRequest behavior.

* **withCredentials** - `{boolean}` - whether to set the `withCredentials` flag on the XHR object. See [requests with credentials](https://developer.mozilla.org/docs/Web/HTTP/Access_control_CORS#Requests_with_credentials) for more information.
* **responseType** - `{string}` - see [XMLHttpRequest.responseType](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#xmlhttprequest-responsetype).

