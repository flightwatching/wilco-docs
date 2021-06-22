---
description: 'FW.setLoc(locOrReg, d, reg)'
---

# FW.setLoc

Sets the location of a the current event's Fwot.

If `locOrReg` is a string, then it should be the registration of any other fwot. If it is an array, it should be `[lat, lon, alt]` or `[lat, lon]`

`d` is the date of the position \(moment, date, long or UTC string in the ISO format\)

`reg` is the registration of the fwot we want to put the location on. If not set, then the event's fwot is updated.

```javascript
await FW.setLoc('VHHH') // would put the current fwot to the lication of the airport of HongKong
```

