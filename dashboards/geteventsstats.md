---
description: 'WILCO.getEventsStats(reg, req)'
---

# WILCO.getEventsStats

return event statistics on a fwot. The results can be aggregated

{% hint style="info" %}
This request is aggregated when it is called several times, for example on fleet views. It makes the server optimized.
{% endhint %}

```javascript
const stats = await WILCO.getEventsStats(FWOT.reg, 
  {
//	severities: ["WARNING"],
    tags: this.tags,
  	from: this.momentWindow[0].format('YYYY-MM-DDTHH:mm:ss'),
  	to: this.momentWindow[1].format('YYYY-MM-DDTHH:mm:ss'),
  	dismissed: false,
    aggregates: [{
		kind: "TAG"
	}]
  }
);
```



Here are an example of requests and responses to the new API endpoint :

* Job ALL-COUNT : count all events
* Job DATE-RANGE : count all events between two dates
* Job AFTER : count all events after a date
* Job BEFORE : count all events before a date
* Job KNOWN-REG: count all the events of reg FW-LUC
* Job KNOWN-TAG: count all the events tagged REP2
* Job SEVERITY-INFO: count all the events with the severity INFO
* Job AGGR-REG: count all the events, aggregate results by reg
* Job AGGR-TAG: count all the events, aggregate results by tags
* Job AGGR-SEV: count all the events, aggregate results by severity
* Job AGGR-REG-TAG: count all the events, aggregate results by reg and tag
* Job COMBINED: count all the events between two dates that have the severity INFO and are tagged FLYING, aggregate results by reg



Client request:

```javascript
[{
	"id": "ALL-COUNT"
}, {
	"id": "DATE-RANGE",
	"from": "2019-02-06T10:47:51",
	"to": "2019-02-08T10:47:51"
}, {
	"id": "AFTER",
	"from": "2019-02-08T10:47:51"
}, {
	"id": "BEFORE",
	"to": "2019-02-06T10:47:51"
}, {
	"id": "KNOWN-REG",
	"regs": ["FW-LUC"]
}, {
	"id": "KNOWN-TAG",
	"tags": ["REP2"]
}, {
	"id": "SEVERITY-INFO",
	"severities": ["INFO"]
}, {
	"id": "AGGR-REG",
	"aggregates": [{
		"kind": "REG"
	}]
}, {
	"id": "AGGR-TAG",
	"aggregates": [{
		"kind": "TAG"
	}]
}, {
	"id": "AGGR-SEV",
	"aggregates": [{
		"kind": "SEVERITY"
	}]
}, {
	"id": "AGGR-REG-TAG",
	"aggregates": [{
		"kind": "REG"
	}, {
		"kind": "TAG"
	}]
}, {
	"id": "COMBINED",
	"from": "2019-02-06T10:47:51",
	"to": "2019-02-08T10:47:51",
	"tags": ["FLYING"],
	"severities": ["INFO"],
	"aggregates": [{
		"kind": "REG"
	}]
}]
```



Server response:

```javascript
[{
	"id": "ALL-COUNT",
	"result": {
		"count": 2
	}
}, {
	"id": "DATE-RANGE",
	"result": {
		"count": 2
	}
}, {
	"id": "AFTER",
	"result": {
		"count": 0
	}
}, {
	"id": "BEFORE",
	"result": {
		"count": 0
	}
}, {
	"id": "KNOWN-REG",
	"result": {
		"count": 2
	}
}, {
	"id": "KNOWN-TAG",
	"result": {
		"count": 1
	}
}, {
	"id": "SEVERITY-INFO",
	"result": {
		"count": 1
	}
}, {
	"id": "AGGR-REG",
	"result": {
		"FW-LUC": {
			"count": 2
		}
	}
}, {
	"id": "AGGR-TAG",
	"result": {
		"REP2": {
			"count": 1
		},
		"FLYING": {
			"count": 1
		}
	}
}, {
	"id": "AGGR-SEV",
	"result": {
		"NULL": {
			"count": 1
		},
		"INFO": {
			"count": 1
		}
	}
}, {
	"id": "AGGR-REG-TAG",
	"result": {
		"FW-LUC": {
			"REP2": {
				"count": 1
			},
			"FLYING": {
				"count": 1
			}
		}
	}
}, {
	"id": "COMBINED",
	"result": {
		"FW-LUC": {
			"count": 1
		}
	}
}]
```

