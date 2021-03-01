---
description: Display configurable tables
---

# Tables

![](../.gitbook/assets/image%20%281%29.png)

A table is a set of configurable columns that represents events fields or sample fields.

it can be accessed with this kind of URL: _https://site.flightwatching.com/wilco/\#/table/20303938?page=1&count=100&tag=SUSPECTED&tag=CONFIRMED&tag=IGNORED&tag=CLOSED_ where `20303938` is the ID of the table as per general admin. You can filter out the elements with some query parameters.

Then each row is an event. The events can be filtered and sorted with the URL query, or have a default setting in the configuration. 

You can create as many table as you want, as you can do with dashboards and trends.

The configuration are stored in the general admin

![](../.gitbook/assets/capture-de-cran-2021-01-13-a-18.27.08.png)

{% hint style="info" %}
> For the moment, there is no HMI to edit the JSON configuration
{% endhint %}

