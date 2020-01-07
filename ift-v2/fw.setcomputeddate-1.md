---
description: 'FW.setComputedDate(date, setBeforeTransmissionDate)'
---

# FW.setComputedDate\(\)

Sets the event's computedDate to `date`

Date has to be a moment.utc\(\) format to ensure local time is not in the middle.

`setBeforeTransmissionDate` is a boolean. If `false`, that's it. If `true`, then if the `date` is after the transmissionDate of the event, will shift the date for 1 day \(prevents the round midnight effects\)

