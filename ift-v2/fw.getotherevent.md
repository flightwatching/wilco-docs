---
description: async FW.getOtherEvent(otherEventId)
---

# FW.getOtherEvent

async function that gets an eventV3io from the ID.

For example, if you want to know if a fault code comes from a PFR or a CFR, you can do like this \(in a Fault code IFT\)

```javascript
const flightReport = await FW.getOtherEvent(FW.getEvent().dataId);
if (flightReport.category!='pfr' && fwot.properties.QRT!='special') {
   await FW.uplink(38780026, 0);
  await FW.email('support@flightwatching.com', 'uplinking by CONFSCRIPT because FAULTCODE received in a '+flightReport.category);
}
await FW.tag("ITM30");
```

