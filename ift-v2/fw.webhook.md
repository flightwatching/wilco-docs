---
description: 'await FW.webhook(webhookId, payload, eventId)'
---

# FW.webhook

If you have a web connector \(see layouts\), you can call it in `push` mode from an IFT thru this function. All the IFTs of this webhook will be trigged, as if an external process had. You will not need to specify an `api-key` as it is often mentionned, as we are working locally serverside

* `webhookId`: the ID of the webhook \(a big uuid\) or the name of the webhook. In the below example, `webhookId` can either be `01eb566a-9eef-4773-ae4c-15971cded9fa` or `XLSX_FAULT2FIN`. Be careful when using the name of the layout as a user can change it and can be not unique!!! In that case, the behavior is not predictable!!
* `payload` &lt;optional&gt; is an object that will be injected as the IFT variable. In the below example, the payload would be injected in a variable named `infos`
* eventId: &lt;optional&gt; is the ID of the event the webhook will be run against \(it will be injected into the [EVT](fw.getevent.md) of the webhook\). If not passed,  the IFT's EVT will be propagated.

{% hint style="info" %}
Webhooks are useful in this context to factorize code and reuse it in other IFTs \(different layouts, etc...\)
{% endhint %}

![](../.gitbook/assets/image%20%2814%29.png)

