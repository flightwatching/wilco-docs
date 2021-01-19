---
description: A  set of useful functions that are already packed for you
---

# Utils

## getTag\(tag, event\)

If the tag is found in the event, then it is returned \(the String, that is equal to the `tag` parameter\). Else `null` is returned.

```text
if (getTag('IFT_MAIL', EVT)) {
  WILCO.alertInfo("a mail has been sent with along this event")
} else {
  WILCO.alertInfo("no mail sent")
}
```

{% hint style="info" %}
`EVT` is a variable that exists on all the dashboards related to an event. it does not exists on fleet dashboards, for example. But the event could come from another request
{% endhint %}

