---
description: FW.getFwot(reg)
---

# FW.getFwot\(\)

Access any FWOT using its registration. returns a [FwotV3IO](https://github.com/flightwatching/wilco-api/blob/master/java/com/fw/wilco/api/FwotV3IO.java):

```javascript
await FW.updateSomeFwotProperty('FW-LUC', 'key', 'oldValue');
await FW.updateSomeFwotProperty('FW-LUC', 'key', await FW.getFwot('FW-LUC').properties.key+' newValue');

//would set the property **key** of FW-LUC to **oldValue newValue**
```

###  ``

