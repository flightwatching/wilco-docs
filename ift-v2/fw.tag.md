---
description: 'FW.tag(tag, eventId)'
---

# FW.tag

tags the event with tag; If called several times, tag remains unique \(no effect\)

If the eventId is not passed or null, then the current event is tagged

{% hint style="info" %}
It is strongly recommended to use the await keyword to avoid IFT collision
{% endhint %}

```javascript
await FW.tag("ITM36");
```

{% hint style="info" %}
Like for twitter, the tags are always uppercase. If you enter a lower case, it will be transformed to uppercase on the fly, before saving
{% endhint %}

