# Automatically handle faultcodes according to a doc and a regex

new faultcodes are arriving constantly, and created on the fly. They do appear as a code in the timeline when they are new. It is necessary to describe them manually, to have a clean timeline, and even handle the specific IFTs by hand.

This code makes things generic, if it is set as an IFT of the message holder \(CFR,  PFR, AHM output...\)

```javascript
//we get all the faultcodes
const fcs = FW.getEvent().analysis;
for (const fc of fcs) {
  const event = (await FW.api.get(`events/${fc}`)).data;
  const fc49 = event.tags.find(t=>t.id.match(/49....../))
  if (fc49) {
    // we found a FC that starts with 49
    FW.log(event);
    const docId = 78211586;
    const doc = await FW.csv(docId, {delimiter:';'});
    if (!doc.find(row=>row.MM_CODE==fc49.id)) {
      FW.email(ADMIN,fc49.id+' received but not in the FC description document#'+docId);
    } else {
      // do the specific that is described in the doc
    }
  } else {
    event.visible = false
    FW.api.put(`events/${event.id}`, event)
  }
}

```

