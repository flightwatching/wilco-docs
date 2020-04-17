---
description: Sends some uplinks to the A/C
---

# WILCO.uplink

```javascript
await WILCO.uplink("FW-PAU", 2514563);
```

Will immediately uplink the layout `#2514563` to the aircraft `FW-PAU`

```javascript
await WILCO.uplink("FW-PAU", 2514563, ['sequence:ABC','tieback:AZERTY']);
```

Will immediately uplink the layout `#2514563` to the aircraft `FW-PAU` passing to the uplink template 2 variables named `sequence`and `tieback`with the associated value \(after the colon\)

