---
description: 'FW.uplink(layoutId, delayInSec, opts)'
---

# FW.uplink

Uplinks a message to the current FWOT.

{% hint style="info" %}
The uplink is actually done if the `doUplink` appConfig is set to `true`

If not, the uplink will not fail but the command has no effect.
{% endhint %}

* `LayoutId` is the ID of the layout that you want to uplink. The layout is uplinkable if it specifies a uplink-template in the admin area. The uplink-template may support some options that can be passed as third argument
* `delayInSec` is the number of seconds WILCO have to wait before actually sending the message
* `opts` is an array of strings. each string has the format `key:value`

![The uplink is actually performed if the doUplink is set to true and the uplinkTemplate is set as shown here](../.gitbook/assets/image%20%283%29.png)

```javascript
//uplink the layout 686787 in 20 seconds with the option tieback set to HKG5MN
FW.uplink(686787, 20, ['tieback:HKG5MN']);
```



