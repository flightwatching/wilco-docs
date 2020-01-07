---
description: FW.setComputedDate(date|moment|ISO8601)
---

# FW.setComputedDate\(\)

sets the computed date. If some samples were previously created in the event, their date remains unchanged unless they have `timelabel=AT_EVENT`

`date` has to be a moment.utc\(\) format to ensure local time is not in the middle.

`setBeforeTransmissionDate` is a boolean. If `false`, that's it. If `true`, then if the `date` is after the transmissionDate of the event, will shift the date for 1 day \(prevents the round midnight effects\)

```javascript
FW.setComputedDate(moment.utc(X, 'DDMMYYHHmmss'), false);
```

