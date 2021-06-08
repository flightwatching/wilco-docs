---
description: allows to create global filters on the table
---

# filters

## tags

tags is an array of array of strings. Each leaf array contains the tags for a given group of tags. Grouping is useful in the HMI to gather tags with the same semantic. Clicking on a tag will filter on the tag only. Clicking on multiple tags will select all the events with all of them

{% hint style="info" %}
If you pass some tags in the URL \(?tag=toto\), then a block is created with those tags
{% endhint %}

```javascript
{
  "filters": {
    "tags": [
      [
        "NEW",
        "WATCH",
        "CLOSED"
      ],
      [
        "SUSPECTED",
        "REJECTED",
        "CONFIRMED"
      ],
      [
        "FB_READY",
        "FB_NOT_READY"
      ]
    ]
  },
  "cols": [
  ...
  ]
  }
```

![](../../.gitbook/assets/image%20%2812%29.png)

