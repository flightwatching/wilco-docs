---
description: Sends an email
---

# FW.email

```javascript
await FW.email (dest, subject, options = {cc:null, bcc:null, body:{text:""}, attachments:[]})
```

* `dest`: a string that is a comma separated list of email addresses \(recipients\)
* `subject`: a string that will be the subject of the mail
* `opts`: an optional object. Each option is optional.
  * `cc`: string that is a comma separated list of email addresses \(carbon copy\)
  * `bcc`: string that is a comma separated list of email addresses \(blind carbon copy\)
  * `body`:
    * `text`: if the body is plain text. `\n` is the character for a new line
    * `docId`: the id of a document in wilco \(see /fleet/admin/docs\). The document is either a static file or a template \(see `variables`\)
    * `variables`: a key value structure that will be passed to the doc \(`docId`\) to instanciate the template
  * `attachments`: an array of attachment. an attachment is an object with those values
    * `absolutePath`: the path of the file you want to attach. WARNING: it is the path in the server. So it is not directly readable from your client. The only usecase is the snapshot usecase \(see below\)
    * `docId`: the id of a document in wilco \(see /fleet/admin/docs\). The document is either a static file or a template \(see `variables`\)
    * `variables`: a key value structure that will be passed to the doc \(`docId`\) to instanciate the template

## Example of template doc

Note that the template email that is hosted by the `docId` is a groovy template. It means that the variables can be referenced like this:

```javascript
await FW.email ("laurel@hal-roach.com, hardy@hal-roach.com", 
"the subject", {
body: {
    docId: 83391, 
    variables: {
        rep: "POST FLIGHT REPORT", 
        mm: {code: "1234F567", text: "PROBLEM WITH..."},
        rev: "XX-YYYY",
        FIM: "AA-BB-CC"
    }
} 
})
```

```markup
<h3>
	<p>${subject}</p>
</h3>
<hr>
<p>${sub} </p>
<hr>
<h3><i>EVENT DESCRIPTION</i></h3>
<ul>
	<li><i>REPORT:</i> ${rep} </li>
    <li><i>Maintenance Message:</i> ${mm?.code} : ${mm?.text}</li>
</ul>
<h3><i>FOR REFERENCE ONLY</i></h3>
<i>Per Fault Isolation Manual: Rev Date </i>: ${rev}
<ul>
    <li><p><i>Associated FIM TASK:</i> ${FIM}</p></li>
</ul>
<hr>    
```

## Examples of calls:

* simplest call: `await FW.email ("laurel@hal-roach.com, hardy@hal-roach.com", "the subject")`
* simplest call with body: `await FW.email ("laurel@hal-roach.com, hardy@hal-roach.com", "the subject", {body: {text: "this is the body"} })`
* a call with a template as body and a `cc`: `await FW.email ("laurel@hal-roach.com, hardy@hal-roach.com", "the subject", {cc: "sales@fox.com", body: {docId: 83391, variables: {a: 1, b: {sub1: "my first option", sub2: my second option}}} })`
* a call with a template as attachment: `await FW.email ("laurel@hal-roach.com, hardy@hal-roach.com", "the subject", {body: "the body", attachments: [{docId: 83391, variables: {a: 1, b: {sub1: "my first option", sub2: my second option}}} }])`

### Snapshot as attachments! \(beta\)

Now, from an IFT, you can snapshot a WILCO page. It will create a PDF file containing the screenshot corresponding to the passed URL.

You can therefore add this file as an attachment to any email.

```javascript
const file = await FW.snapshot('https://mysite.flightwatching.com/fleet/apiv3/status');
const opts = {body: {text: 'my body'}, attachments: [{absolutePath: file}]};
await FW.email('laurel@hal-roach.com', 'a snap created', opts);
```

