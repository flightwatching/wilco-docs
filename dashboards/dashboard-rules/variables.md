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

Some predefined fields are allowed acording to the page where the dashboard is inserted:

<table>
  <thead>
    <tr>
      <th style="text-align:left">What page</th>
      <th style="text-align:left">Field name</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Fleet page</td>
      <td style="text-align:left">db</td>
      <td style="text-align:left">the <code>id</code> of the dashboard</td>
    </tr>
    <tr>
      <td style="text-align:left">Fleet page</td>
      <td style="text-align:left">cols</td>
      <td style="text-align:left">the count of dashboard copies per row</td>
    </tr>
    <tr>
      <td style="text-align:left">Fleet page</td>
      <td style="text-align:left">refDate</td>
      <td style="text-align:left">
        <p>A date that is the latest date for the requests. Makes it possible to
          have fleet status in the past. Please note that even if <code>refDate</code> is
          set, the status of the FWOT is still the current one, not at <code>refDate</code>
        </p>
        <p>To parse, we first check if the string matches known <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> formats,
          we then check if the string matches the <a href="https://tools.ietf.org/html/rfc2822#section-3.3">RFC 2822 Date time</a> format</p>
        <p>If not set, the date is now</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Fleet page</td>
      <td style="text-align:left">count</td>
      <td style="text-align:left">A number that works in conjunction with <code>unit</code> if not provided,
        default is 100.</td>
    </tr>
    <tr>
      <td style="text-align:left">Fleet page</td>
      <td style="text-align:left">unit</td>
      <td style="text-align:left">a time unit to define the time windows for the display. can be one of
        <a
        href="https://momentjs.com/docs/#/manipulating/add/">https://momentjs.com/docs/#/manipulating/add/</a>
      </td>
    </tr>
  </tbody>
</table>

{% hint style="info" %}
Example: fleet?db=13662458&cols=12&count=5&unit=days&airport=VHHH&refDate=2020-01-14

the request would be on all the samples between the 09 of Jan to the 14th
{% endhint %}

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

