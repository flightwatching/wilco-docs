---
description: 'FW.set(param, value, timestamp)'
---

# FW.set\(\)

creates a sample for the passed parameter. if timestamp is not passed, then the event timestamp is used



* `param` is a string and is the name of the parameter that will be created. If the parametre does not exists, it will be created on the fly
* `value` is the value of the parameter. It can be a number or a string
* The `timestamp` has to be in the format: "yyyy-MM-dd'T'HH:mm:ss" or a date or a moment or any ISO9001 format. if timestamp is not passed, then the event timestamp is used

```javascript
if (APUBV=="-"||APUBV=='X') {
  await FW.set("LS_APU_NA",0);
} else if(+APUBV==1) {
	await FW.set("LS_APU_NA",100);
}
```

