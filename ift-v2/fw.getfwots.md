---
description: Accesses all the Fwots of Wilco
---

# FW.getFwots\(\)

You can filter it with [\_](http://underscorejs.org/):

```text
const a320s = _.where(FW.getFwots(), {type:'A320'});
```

returns an array of [FwotV3IO](https://github.com/flightwatching/wilco-api/blob/master/java/com/fw/wilco/api/FwotV3IO.java):

```text
FW.updateSomeFwotProperty('FW-LUC', 'key', 'oldValue');
FW.updateSomeFwotProperty('FW-LUC', 'key', FW.getFwot('FW-LUC').properties.key+' newValue');

//would set the property **key** of FW-LUC to **oldValue newValue**
```

###  ``

