---
description: >-
  This app config is a json structure (an array). It contains ordered elements
  that will run the routing policy of the uplinks.
---

# UPLINK\_ROUTING

WILCO has 2 gateways to uplink the A/C, and they allow to uplink the A/C either on the ARINC network either on the SITA network. Normally, there is a megaswitch that makes the 2 networks interconnected, but sometimes we need to route explicitely to one of those network (cost management, megaswitch bugs, etc...)

Additionally, some customers want a dedicated way to uplink, for example thru their facility. iin that case, we can propose a dedicated route. for the moment, only local directory is supported. It can be a SFTP directory, or a remote one...

Sometimes also, we'd like to test or develop, or make research and development. It is therefore important to isolate an airline or a set of A/C

Each uplink route looks like this

* a filter that may be the fwot or the airline. It is a regex
* a gateway that can be `SDC` (SITA), `AVINET` (ARINC) or `LOCALFILE` (local directory)

> the routes are evaluated in the order of the index in the array. the first matching rule is applied for the current A/C, the next ones are not even evaluated

Of course, there is a fallback behavior, that WILCO handles by choosing dynamically the gateway if not specified here



```json
[
    {
        "fwot": "FW-R.+",
        "gateway": {
            "type" : "SDC"
        }
    },
    {
        "airline": "AFR",
        "gateway": {
            "type": "AVINET"
        }
    },
    {
        "airline": "CCX",
        "gateway": {
            "type": "LOCALFILE",
            "path": "/tmp/ftp/place/ou/stocker/le/fichier"
        }
    },
    {
        "airline": "ETH",
        "gateway": {
            "type": "NONE"
        }
    }
]
```

