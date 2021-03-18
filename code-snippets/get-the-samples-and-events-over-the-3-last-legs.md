---
description: Not easy to grab the history and play on a time range. Example
---

# get the samples and events over the 3 last legs

```javascript
const e = FW.getEvent();
const toDate = e.computedDate;
const legCount=3;

//GET THE TIME RANGE
//==================

//on récupere les OOOI. Le mieux serait de tagger LEG le début d'un leg, et faire la recherche sur LEG plutot que OOOI
// ca éviterait de chercher N OOOIs de filtrer après
const ooois = await FW.getEvents(e.reg, null, toDate, true, false, null, ["OOOI"], 20);

// we have the date of n legs before now
const fromDate = ooois.filter(o=>o.sumUp=='OFF').map(o=>o.computedDate)[legCount-1];
  
  
//PLAY WITH SAMPLES
//=================
  
//gets the sample of PRV_1 in this time range
const samples = await FW.querySamples(null,['PRV_1'],fromDate, toDate ,false,false,1,10000);
//now we have a list of samples between those dates. we can play with it
// how many times the PRV_1 is opened?
FW.log(samples.filter(s=>+s.value>0).length);
  
  
//PLAY WITH EVENTS
//==================
//gets the  ATA21 messages between those dates
const ata21 = await FW.getEvents(e.reg, fromDate, toDate, true, false, null, ["ATA21"], 10000);
// play with it: how many occurences?
FW.log(ata21.length);
```

