---
description: Accessing the samples in your IFT
---

# Samples

The samples for the currently processed message or constants are provided in the script for computation. A variable is automatically created for each sample or constant. The variable contains the value of the sample as a string, whatever the status. To use it as a number, just add the sign _+_ before it.

```javascript
var EGT_1="655"; //created by WILCO
var EGT_2="658"; //created by WILCO

//can be used like this:

var EGTdiff = Math.abs(+EGT_1-EGT_2);
```

{% hint style="info" %}
If the name of the variable cannot be a javascript variable \(contains spaces, is only a sequence of numbers, contains special characters\), this variable is not created.n any case, the sample can be accessed with the `FW` object. And this time it is the sample as an object with [those fields](https://github.com/flightwatching/wilco-api/blob/master/java/com/fw/wilco/api/SampleV3IO.java)
{% endhint %}

You can for example do this:

```javascript
if (FW["EGT_1"].state=="VALID" && FW["EGT_2"].state=="VALID" ) {
  FW.setStyle('color', 'SpringGreen');
  var EGTdiff = Math.abs(+FW["EGT_1"].value-FW["EGT_2"].value);
}
  FW.setStyle('color', 'RED');
}
```

###  ``

