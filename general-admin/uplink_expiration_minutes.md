# UPLINK\_EXPIRATION\_MINUTES

Old uplinks expires \(when sent to ARINC network\). 

It avoids old uplinks to be sent to the A/C, in case of a stall in the system, and burst the uplink rate when restart, with obsolete responses.

This is the default max lifetime of an uplink in minutes \(birth is request date\). 

{% hint style="info" %}
If not set, the default is 30 minutes
{% endhint %}

