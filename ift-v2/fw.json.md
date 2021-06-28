---
description: FW.json(docId)
---

# FW.json

reads an XLSX document stored in Wilco, and converts it to json according to the parameter passed

* docId : Id of the document to read

This function is async, it should be used like:

`const xlsx_data = await FW.json(12521215);`

The XLSX document must name each column with an header line as the first line.

For example, an XLSX with two sheets, one named "Jazz" with the following data:

First name;Last name  
Louis;Armstrong  
Keith;Jarrett  
Oscar;Peterson

and an another one with the following data:

First name;Last name  
Paco;de Lucia  
Al;di Meola

will be transformed in the following json:

`{ "jazz": { "content": [{ "first_name": "Louis", "last_name": "Armstrong" }, { "first_name": "Keith", "last_name": "Jarrett" }, { "first_name": "Oscar", "last_name": "Peterson" }], "columns": ["first_name", "last_name"] }, "flamenco": { "content": [{ "first_name": "Paco", "last_name": "de Lucia" }, { "first_name": "Al", "last_name": "di Meola" }], "columns": ["first_name", "last_name"] } }`

