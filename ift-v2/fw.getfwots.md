---
description: Accesses all the Fwots of Wilco
---

# FW.getFwots

{% hint style="info" %}
You have to call this function with the `await` javascript keyword in order to be sure to have the list from the server to continue
{% endhint %}

You can filter it with [\_](http://underscorejs.org/):

```javascript
const a320s = _.where(await FW.getFwots(), {type:'A320'});
```

returns an array of [FwotV3IO](https://github.com/flightwatching/wilco-api/blob/master/java/com/fw/wilco/api/FwotV3IO.java):

```javascript
await FW.updateSomeFwotProperty('FW-LUC', 'key', 'oldValue');
await FW.updateSomeFwotProperty('FW-LUC', 'key', await FW.getFwot('FW-LUC').properties.key+' newValue');

//would set the property **key** of FW-LUC to **oldValue newValue**
```

### `` ``
