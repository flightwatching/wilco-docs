# Fields of a column

## title

A text field that will be the displayed text in the header of the table

{% hint style="info" %}
Title is optional. Sometimes you want to dig into the table directly
{% endhint %}

## param

A string that is the field of the event/sample to display. 

The source of the field \(event/sample\) depends on the `source` : if the source is `event`, then it is a field of [here](https://app.swaggerhub.com/apis/flightwatching/wilco-api/3.0.0#/EventV3IO). If it is a `sample`, it its its value

{% hint style="info" %}
You can also specify an array of strings. In that case, the fields are tried from the first to the last until a non null value is found. This is particularly useful when the title and the sumUp may contain the information.
{% endhint %}

## source

Authorized values are `event` or `sample`. if `event`, then the param is a field of the event. If `sample`, then it is the name of a sample that belongs to the event

## type

type is the type of the value held by the param. it can be `tags`, `fwot`, `text`, `date`

## filter

for tags type, the filter limits the list to the given array of strings.

## behavior

`RADIO` means that only one of the tags that are in the filter can live at the same time: if you click on one tag to set it, the others are automatically removed

`TOGGLE` means that each tag that are displayed are independent and several of them can live together

## editable

a boolean \(true or false\) saying that the cell can be edited or not. Some of the fields are not editable by nature: the id of a event, the fwot, etc... In that case, the field is ignored



