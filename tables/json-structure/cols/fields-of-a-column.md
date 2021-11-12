# Fields of a column

## title

A text field that will be the displayed text in the header of the table

{% hint style="info" %}
Title is optional. If not set, the param is displayed
{% endhint %}

## param

A string that is the field of the event/sample to display.&#x20;

The source of the field (event/sample) depends on the `source` : if the source is `event`, then it is a field of [here](https://app.swaggerhub.com/apis/flightwatching/wilco-api/3.0.0#/EventV3IO). If it is a `sample`, it its its value

{% hint style="info" %}
You can also specify an array of strings. In that case, the fields are tried from the first to the last until a non null value is found. This is particularly useful when the title and the sumUp may contain the information.
{% endhint %}

## source

Authorized values are `event` or `sample`. if `event`, then the param is a field of the event. If `sample`, then it is the name of a sample that belongs to the event

## type

type is the type of the value held by the param. it can be `tags`, `fwot`, `text`, `date`, `list`

![tags: all the tags of the filter are displayed. click on it to (un)select it](<../../../.gitbook/assets/image (9).png>)

![list: the selected tags only are displayed. The others are collapsed in a dropdown list. Usefull when there are many elements](<../../../.gitbook/assets/image (5).png>)

![fwot: displays the fwot with this precreated format. Click brings the user to the timeline @ correct time](<../../../.gitbook/assets/image (7).png>)

![date: date comes along with format field](<../../../.gitbook/assets/image (8).png>)

## filter

for tags type, the filter limits the list to the given array of strings.

## behavior

`RADIO` means that only one of the tags that are in the filter can live at the same time: if you click on one tag to set it, the others are automatically removed

`TOGGLE` means that each tag that are displayed are independent and several of them can live together

## editable

a boolean (true or false) saying that the cell can be edited or not. Some of the fields are not editable by nature: the id of a event, the fwot, etc... In that case, the field is ignored

## onedit

a string which is the webhook that will be called when the cell is edited (at the end of the process).  It should be a WEB connector layout. The webhook is called (POST) with the `eventId` in the query parameters, and a payload (see below):

if `onedit: layouts/webhook/XXX-a9cf-4092-a619-431d0e2a056c ` wilco calls \`POST `` layouts/webhook/XXX-a9cf-4092-a619-431d0e2a056c?eventId=263572` `` where `263572` is the event id of the current line displayed

The payload is the following:

```json
{
    column: h, //the current column definition (with all the fields described in this documentation
    action: action, //can be TAG or UNTAG
    data: tag, // the current tag being set
    user: user, // the current user (login, role...)
    eventBundleId: // the current event bundle id
}
```

## format

a string that describes the format of the `date` The format syntax is described [here](https://momentjs.com/docs/#/displaying/)

## pattern

A [regex](https://www.w3schools.com/js/js\_regexp.asp) that limits the possibilities for the edition of a cell. For example, force a number, uppercases, a count of letters, etc...
