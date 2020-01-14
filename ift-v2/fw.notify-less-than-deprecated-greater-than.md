---
description: 'FW.notify(who, subject, body)'
---

# FW.notify &lt;deprecated&gt;

Sends an e-mail to `who` with subject and eventually a body. A signature is always added to the message. It can be overridden with the AppConfig property `MAIL_TEMPLATE` using the groovy syntax \([cheatsheet](https://www.playframework.com/documentation/1.5.x/cheatsheet/templates)\). Few parameters are available.

```groovy
Check ${msg.sumUp} details <a href="${url}">here</a>
<br>
<br>
<em>Health Monitoring by Flightwatching</em>
```

```javascript
await FW.notify('support@flightwatching.com', //recipient list
'My subject', // subject
'Dear FW support team, ...' //body
);
```

* `who`: A string with brackets, coma or semicolon separator of email addresses. The function will create the array of recipients from it. any field that does not contains the character @ will be ignored
* `subject`: the subject of the email
* `body`: the content of the message.

###  ``

