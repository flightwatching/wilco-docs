# Access to the surrounding values

Trends comes with a handy function getAround. For each point, it returns an array with the surrounding values. This is useful to measure derivatives or max/min/averages... with standard Javascript

`getAround(name, countBefore, countAfter)`

* name: the name of the parameter as string
* countBefore: the count of samples to get before the current point
* countAfter: the count of samples to get after the current point

```javascript
// smothes the trend by averaging the last 4 samples. Current value is 9.1
// getAround returns ["2.6", "11.4", "2.6", "9.1"]
if(DELTA_PACK_P>0){
	return getAround("DELTA_PACK_P", 3, 0).mean();
}
```

{% hint style="danger" %}
Be careful as the name of the parametre is a string. If you do not mention the parameter as a variable in the formula, then WILCO will not fetch it from the database.

The following would not work

```javascript
return getAround("DELTA_PACK_P", 20, 0).mean();
```

In those simple cases, you will have to mention explicitely the variable, for example like this:



```javascript
const toto=DELTA_PACK_P;
return getAround("DELTA_PACK_P", 20, 0).mean();
```
{% endhint %}

