---
description: >-
  WILCO automatically sets some variables as the context of the call of any
  dashboard rule
---

# Variables

#### scope.anims

A dictionnary with all the `_anims`. The key is the name of the anim, and the value is the anim itself.

#### scope.samples

even if the samples are accessible one by one, you may want to have an object with each one. The `scope.samples` object is for you. Each property is the sample name, and value is the value. You will have all mixed together: constants, samples, and general object \(see below\)

```javascript
{
    TAV_LIMIT: 70, 
    COT_MAX: 220, 
    CABIN_TEMP_HOT: 28, 
    OXY_LO: 1150, 
    EVT: {id: "25123609", klass: "CFD", category: "CFD", tags: Array(0), transmissionDate: "2020-04-09T15:17:00", …},
    FWOT: {reg: "B-XXX", coolName: "", category: "aircraft", type: "A330", status: "pwrup", …}
    …
}
```

{TAV\_LIMIT: 70, COT\_MAX: 220, CABIN\_TEMP\_HOT: 28, OXY\_LO: 1150, ENG\_OIL\_LO: 17, …}



#### URL\_PARAMS

an object containing all the url parameters. for example `http://localhost:9000/#/APUs/events/807885?timeUnits=weeks&reg=FW-RVL` will provide the object

```text
{
	"timeUnits":"weeks",
	"reg":"FW-RVL"
}
```

#### EVT \(use this for a given event\)

`EVT` is an object that represents the [EventV3IO API object](https://github.com/flightwatching/wilco-api/blob/master/java/com/fw/wilco/api/EventV3IO.java). you can access the fields like this:

```text
var theCurrentDate = EVT.computedDate;
//use the variable (display...)
```

the dates are strings of formatted dates in ISO format \(e.g 2014-11-26T23:56:12\) you can use [moment.js](http://momentjs.com/docs/) to process it

```text
var date = moment(EVT.computedDate)
date.format("dddd, MMMM Do YYYY, h:mm:ss a"); // "Sunday, February 14th 2010, 3:25:50 pm"
date.fromNow(); // 4 hours ago
```

#### FWOTS

`FWOTS` is an array of known FWOTs \(like in fleet view\). The format of each is the same as [FwotV3IO API object](https://github.com/flightwatching/wilco-api/blob/master/java/com/fw/wilco/api/FwotV3IO.java) you can loop on the FWOT array with a standard javascript loop

```text
for (var i = 0; i < FWOTS.length; i++) {
	var fwot = FWOTS[i];
	//do the stuff...
};
```

#### FWOT

`FWOT` contains the current FWOT that is represented in the thumbnail \(see [FwotV3IO API object](https://github.com/flightwatching/wilco-api/blob/master/java/com/fw/wilco/api/FwotV3IO.java)\)

```text
MY_anim.go().text(FWOT.reg);
```

if you want to select an aircraft \(for example the current event one\) you can use underscore to avoid the loop

```text
	var acEvts=_.where(evts, {reg: EVT.reg});
```

Each sample is described below

#### DATE \(event scope only\)

contains the current date in unix timestamp e.g 1381295944000. This is useful to display the current date in the SVG and to compare the current date with the sample date and check if the sample is right on the current date or is from a near timestamp.

you can compare it with DATE == TAT.date or using momentjs.

