---
description: FW.setTitle(title)
---

# FW.setTitle

You can override the default title for any event in an IFT. You can compose the title with the context of the event. Here is a sample:

{% hint style="info" %}
Prefer it to `FW.reportInfo()` function for simple text information
{% endhint %}

```javascript
if (TRIGGER_CODE==='8100') {
  await FW.setTitle('ECS REPORT<19> (UPK)')
}
```

![](../.gitbook/assets/settitle.png)

