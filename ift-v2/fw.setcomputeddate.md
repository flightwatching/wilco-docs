---
description: FW.setComputedDate(date|moment|ISO8601)
---

# FW.setComputedDate\(\)

sets the computed date. If some samples were previously created in the event, their date remains unchanged unless they have `timelabel=AT_EVENT`

```javascript
FW.setComputedDate(moment.utc(X, 'DDMMYYHHmmss'));
```

