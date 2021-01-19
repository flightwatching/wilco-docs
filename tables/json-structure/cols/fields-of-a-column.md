# Fields of a column

## title

A text field that will be the displayed text in the header of the table

## param

A string that is the field of the event/sample to display. The fields complies to the definition found [here](https://app.swaggerhub.com/apis/flightwatching/wilco-api/3.0.0#/EventV3IO)

The source of the field \(event/sample\) depends on the `source` 

{% hint style="info" %}
You can also specify an array of strings. In that case, the fields are tried from the first to the last until a non null value is found. This is particularly useful when the title and the sumUp may contain the information.
{% endhint %}

## source

Authorized values are `event` or `sample`. if `event`, then the param is a field of the event. If `sample`, then it is the name of a sample that belongs to the event

## type

type is the type of the value held by the param. it can be `tags`, `fwot`, `text`, `date`

