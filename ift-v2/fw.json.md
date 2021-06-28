---
description: FW.json(docId)
---

# FW.json

reads an XLSX document stored in wilco, and converts it to json according to the parameter passed

* docId : Id of the document to read

This function is async, it should be used like:

`const xlsx_data = await FW.json(12521215);`

\`\`

