---
description: >-
  IFTs are busines rules that are run at each message received. It is either
  linked to a layout, or a parameter or a faultcode.
---

# IFT V2

![The business rules are small automations that are trigged by any received message](../.gitbook/assets/image%20%285%29.png)

{% hint style="info" %}
**a pre-requisite is to know javascript.**

Generally speaking, all the calls that have to access the server should be called with the `await` javascript keyword to ensure the modifications are performed server-side before continuing

It is particularly the case when calling for example `fw.tag("A'); fw.tag('b')` because if you do not put the await, the calls could happend in competition and lead to unpredictable result.
{% endhint %}

