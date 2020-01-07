# Get the last UPLINK message with filters

```javascript
//1
const now = moment.utc(FW.getEvent().computedDate);
const TenMinutesBefore = moment.utc(now).add(-10, 'minutes');
//2
const lastAll=(await FW.getEvents(FW.getEvent().reg, TenMinutesBefore, null, false, false, null, ['IFT_UPLINK'], 300));
//3
const lastITM=lastAll.filter(e=>e.tags.map(t=>t.id).includes('ATA78') && e.sumUp.match("RELAY[12]"));

FW.log(lastITM.map(e=>e.sumUp));
```

1. We create a timespan starting 10 minutes ago. The `now` is not the current UTC but is the currently processed message. It is important to use this timestamp as the occurence may be in the past when reparsing the messages or receiving it late.
2. We query the DB for the messages of the same fwot in the time window, filtering for the internal tag `IFT_UPLINK` that is automatically positionned when an uplink is trigged thru IFT. We limit to 300 events, which is totally arbitrary
3. We filter the received results that matches a second tag `ATA78` and which `sumUp` matches RELAY1 or RELAY2

\[FW.getEvents\]\(../ift-v2/fw.getevents\)



