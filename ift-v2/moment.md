---
description: manipulate dates
---

# moment

You can use the very good library [moment](http://momentjs.com/docs/) to manipulate the dates

```javascript
const fromDate = moment.utc(FW.getEvent().computedDate).add(-2, 'days');
```

The function `diff` is often used. Note that the order to use is like if you substracted. If the left is greater than the right, the diff is positive.

```javascript
const now = moment.utc();
const tomorrow = moment(now).add(1, 'day');
FW.log(tomorrow.diff(now))

// returns 86400000
```

