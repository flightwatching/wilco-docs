# IFT V2

{% hint style="info" %}
**a pre-requisite is to know javascript.**

Generally speaking, all the calls that have to access the server should be called with the `await` javascript keyword to ensure the modifications are performed server-side before continuing

It is particularly the case when calling for example `fw.tag("A'); fw.tag('b')` because if you do not put the await, the calls could happend in competition and lead to unpredictable result.
{% endhint %}

