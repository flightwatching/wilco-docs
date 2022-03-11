# FW.http

`FW.http` is a proxy to access any external resources over the web with the HTTP protocole.

It is a wrapper to the fantastic library axios. `FW.http` holds an instance of [https://axios-http.com/docs/instance](https://axios-http.com/docs/instance)

```javascript
try {
  const lastPos = (await FW.http.get("http://aviation-edge.com/v2/public/flights?key=xxx&regNum="+fwot.reg)).data[0];
  FW.log(lastPos)
} catch(error) { 
  FW.log("oops...");
}
```
