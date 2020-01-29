---
description: 'WILCO.dsv(id, delimiter)'
---

# WILCO.dsv

gets a document \(see general admin\) from its id. **The document has to be a delimited array like a CSV file**.

{% hint style="info" %}
Be careful as the documents can be whatever document, text or images or PDF. If you try to open an image or a PDF, you will have an undetermined behavior. 

If the document is huge, it can block your HMI
{% endhint %}

The method is asynchrone and will return an array of objects where the elements represents each the lines. The first line is considered as the header and will be skipped. Nevertheless each value of the header is the name of the field of the line object.

### Example

| **warning** | **ATA** | **side** |
| :--- | :--- | :--- |
| **RELAY1\(39CE1\)/TERTIARY LOCK PCM\(E1-4007EG\)** | **78** | **1** |
| RELAY2\(39CE2\)/TERTIARY LOCK PCM\(E2-4007EG\) | 78 | 2 |
| TR RVT\(E1-4119KS1/2/3/4\)/JUNCTION BX\(E1-4110KS\)A | 78 | 1 |
| TR RVT\(E1-4119KS1/2/3/4\)/JUNCTION BX\(E1-4110KS\)B | 78 | 1 |
| TR STOW SW \(E1-4104KS2\)/JUNCTION BX \(E1-4110KS\) | 78 | 1 |
| TR STOW SW \(E1-4104KS3\)/JUNCTION BX \(E1-4110KS\) | 78 | 1 |
| TR STOW SW \(E2-4104KS1\)/JUNCTION BX \(E2-4110KS\) | 78 | 2 |
| TR STOW SW \(E2-4104KS2\)/JUNCTION BX \(E2-4110KS\) | 78 | 2 |
| TR STOW SW \(E2-4104KS3\)/JUNCTION BX \(E2-4110KS\) | 78 | 2 |
| TR STOW SW \(E2-4104KS4\)/JUNCTION BX \(E2-4110KS\) | 78 | 2 |
| ENG 1 REV UNLOCKED | 78 | 1 |
| ENG 2 REV UNLOCKED | 78 | 2 |
| ENG 1 REV FAULT | 78 | 1 |
| ENG 2 REV FAULT | 78 | 2 |
| TERTIARY LOCK \(E1-4005EG1/2/3/4\) | 78 |  |
| T LOCK\(E2-4005EG1/2/3/4\)/PCM\(E2-4007EG\) | 78 |  |

```javascript
  const doc = await WILCO.dsv(1052657);
  console.table(doc);
/*
    [ {warning: "RELAY1(39CE1)/TERTIARY LOCK PCM(E1-4007EG)", ATA: "78", side: "1"}
 {warning: "RELAY2(39CE2)/TERTIARY LOCK PCM(E2-4007EG)", ATA: "78", side: "2"}
 {warning: "TR RVT(E1-4119KS1/2/3/4)/JUNCTION BX(E1-4110KS)A", ATA: "78", side: "1"}
 {warning: "TR RVT(E1-4119KS1/2/3/4)/JUNCTION BX(E1-4110KS)B", ATA: "78", side: "1"}
 {warning: "TR STOW SW (E1-4104KS2)/JUNCTION BX (E1-4110KS)", ATA: "78", side: "1"}
 {warning: "TR STOW SW (E1-4104KS3)/JUNCTION BX (E1-4110KS)", ATA: "78", side: "1"}
 {warning: "TR STOW SW (E2-4104KS1)/JUNCTION BX (E2-4110KS)", ATA: "78", side: "2"}
 {warning: "TR STOW SW (E2-4104KS2)/JUNCTION BX (E2-4110KS)", ATA: "78", side: "2"}
 {warning: "TR STOW SW (E2-4104KS3)/JUNCTION BX (E2-4110KS)", ATA: "78", side: "2"}
 {warning: "TR STOW SW (E2-4104KS4)/JUNCTION BX (E2-4110KS)", ATA: "78", side: "2"}
 {warning: "ENG 1 REV UNLOCKED", ATA: "78", side: "1"}
 {warning: "ENG 2 REV UNLOCKED", ATA: "78", side: "2"}
 {warning: "ENG 1 REV FAULT", ATA: "78", side: "1"}
 {warning: "ENG 2 REV FAULT", ATA: "78", side: "2"} 
 {warning: "TERTIARY LOCK (E1-4005EG1/2/3/4)", ATA: "78", side: ""}
 {warning: "T LOCK(E2-4005EG1/2/3/4)/PCM(E2-4007EG)", ATA: "78", side: undefined}
 ]
 */
```

{% hint style="info" %}
The underlying method is from d3: [https://github.com/d3/d3-3.x-api-reference/blob/master/CSV.md\#arbitrary-delimiters](https://github.com/d3/d3-3.x-api-reference/blob/master/CSV.md#arbitrary-delimiters)
{% endhint %}



