---
description: FW.getRaw()
---

# FW.getRaw

returns the raw data of the event \(with `await`\). The raw data is a string that you can manipulate with standard javascript String methods.

```javascript
const raw = await FW.getRaw();
if (raw.indexOf('EEC')>0) {
//FW.log(raw)
await FW.email('xxx@my-company.com', 'EEC found in CL3')
}

```

