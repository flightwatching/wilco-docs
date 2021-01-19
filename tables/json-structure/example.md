# Example

```javascript
{
    "cols": [
        {
            "title": "Description",
            "param": [
                "title",
                "sumUp"
            ],
            "type": "text",
            "source": "event"
        },
        {
            "title": "ETOPS",
            "filter": [
                "ETOPS"
            ],
            "type": "tags",
            "behavior": "TOGGLE",
            "source": "event",
            "editable": false
        },
        {
            "title": "A/C",
            "type": "fwot",
            "source": "event",
            "editable": false
        },
        {
            "title": "Trigger date",
            "param": "computedDate",
            "type": "date",
            "source": "event",
            "format": "dd MMM yyyy",
            "editable": false
        },
        {
            "title": "Status",
            "type": "tags",
            "filter": [
                "SUSPECTED",
                "CONFIRMED"
            ],
            "behavior": "RADIO",
            "source": "event",
            "editable": true
        },
        {
            "param": "ATA",
            "source": "sample",
            "editable": false
        },
        {
            "param": "OEMS_RO",
            "source": "sample",
            "editable": false
        },
        {
            "param": "AL_RO",
            "source": "sample",
            "editable": false
        },
        {
            "param": "AL_WO",
            "source": "sample",
            "editable": false
        },
        {
            "title": "links",
            "source": "event",
            "editable": false,
            "links": [
            {
               "target":"event",
               "name": "go",
               "options":{"db":15261529}
            }]
        }

    ]
}
```

