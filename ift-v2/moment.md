---
description: manipulate dates
---

# moment

You can use the very good library [moment](http://momentjs.com/docs/) to manipulate the dates

```javascript
const fromDate = moment.utc(FW.getEvent().computedDate).add(-2, 'days');
```

