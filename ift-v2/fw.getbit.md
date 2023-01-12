---
description: getBit(hex, bit)
---

# FW.getBit

returns the  value (1 or 0) of the bit that is located at the `bit` position in the `hex` hexadecimal string

```javascript
FW.getBit("FFFF0000",1); //returns 1
FW.getBit("FFFF0000",30); //returns 0
FW.getBit(".",1); //returns -2 as error code for not an HEX
FW.getBit("F",0); //returns -1 as index not OK

```

{% hint style="info" %}
The bit position starts at 1
{% endhint %}
