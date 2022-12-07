---
description: A  set of useful functions that are already packed for you
---

# Utils

## getTag(tag, event)

If the tag is found in the event, then it is returned (the String, that is equal to the `tag` parameter). Else `null` is returned.

```javascript
if (getTag('IFT_MAIL', EVT)) {
  WILCO.alertInfo("a mail has been sent with along this event")
} else {
  WILCO.alertInfo("no mail sent")
}
```

{% hint style="info" %}
`EVT` is a variable that exists on all the dashboards related to an event. it does not exists on fleet dashboards, for example. But the event could come from another request
{% endhint %}

## setTag(tag, event, toggleTags)

This util sets a `tag` on the current event (but does not push it to the server)

If the `toggleTags` are passed, they are all removed, exept `tag` which is set. It emulates a radio button behavior

## clickForTrend

## updateFwotProperty

## addSamples

Allows to add some samples injected as variables at runtime.

```javascript
    this.addSamples(a.hits.hits.map (h=>{
      return {
        value: "the value",
        name: 'FWPS_L',
        date: moment("1973-01-01")
      };
    })); // FWPS_L will be injected in the rule.
```

```javascript
my_anim.display(FWPS_L); // FWPS_L exists now.
```

## on new messages

Allows to react on new messages, whatever the fwot it is linked on.

onNewMessages takes a function as a parameter that describes the behavior when a new message is sent. You may filter out all the messages that are not related to the current fwot.

{% hint style="info" %}
Historically, it was bulk of events that were passed. Now it is a single event. You can therefore access to the first element of the array, and the array length is 1 only.
{% endhint %}

```javascript
onNewMessages(evts=>{ 
  if (evts[0].reg==EVT.reg) {
    my_anim.go().text(evts[0].title); 
  }
});
```
