# Webhooks: Get data from typeform and post it to ELK

```javascript
  
// called by a typeform form
// created here: https://admin.typeform.com/form/qDgEpdjU/create
// called from here: https://3if57ibegk0.typeform.com/to/qDgEpdjU
  
moment.locale('fr');
const month = form.form_response.answers[0].choice.label;
const year = form.form_response.answers[1].choice.label;
const type = form.form_response.answers[2].choice.label;
const bill = form.form_response.answers[3].number;
const timestamp = moment.utc(year+month, 'YYYYMMMM').endOf('month');
const doc_id = timestamp.format('YYYYMMDD')+'-'+type;
  
const script = {
  "script" : {
    "source": "ctx._source.bill = params.bill; ctx._source.book2billRatio = (float)(ctx._source.book+22)/(float)params.bill; ctx._source.timestamp = params.timestamp",
    "lang": "painless",
    "params" : {
      "bill" : bill,
      "timestamp": timestamp.format()
    }
  }
};  
  FW.log(script)

var postConfig = {
  method: 'post',
  url: 'https://deployment.ELK.fr/sales/_update/'+doc_id,
  headers: { 
    'Authorization': 'ApiKey XXXXX', 
    'Content-Type': 'application/json'
  },
  data : script
};

  try {
	const response = await axios(postConfig);
	FW.log(JSON.stringify(response.data));
  } catch (e) {
	FW.log(e);
  }
```

