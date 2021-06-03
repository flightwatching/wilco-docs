---
description: >-
  await WILCO.getSampleTableForFwot(reg, params, lastCount, lastUnit, toDate,
  callback)
---

# WILCO.getSampleTableForFwot

same as [`getSamplesForFwot`](wilco.getsamplesforfwot.md) but callback elements are formatted as rows. Callback is like this: `callback(reg,rows)`

`rows` are objects whom each field is the param name and an extra field which is `date`

