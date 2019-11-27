---
description: 'FW.notifyWithTemplate(who, subject, templateId, params)'
---

# FW.notifyWithTemplate\(\) &lt;deprecated&gt;

The purpose of this is to reference the body from a complex html file that will be customized with parameters.

Same as `FW.notify` but the body of the message is created from the template that is passed as parameter.

A template is a document \(in your admin page the `docs` models\). The document file is a text file that will be a html format.

* `templateId` has to be a number \(not a string\) to be considered as a reference to a template.
* `params` is a javascript object that contains all the data used by the template. This object is referenced using the groovy language \([cheatsheet](https://www.playframework.com/documentation/1.5.x/cheatsheet/templates)\)

#### Example

```javascript
await FW.notifyWithTemplate("user1@example.com, user2@example.com", "test template", 48017774, {
  event:{
      id:FW.getEvent().id
    },
    toto:'Japan'
  }
);
```

with template\#48017774 is

```markup
<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title></title>
  </head>
  <body>
  	<h1>HELLO FROM ${toto}</h1>
    <p>The event is #<code>${ event.id }</code></p>
  </body>
</html>
```

###  ``

