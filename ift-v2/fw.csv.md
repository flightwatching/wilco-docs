---
description: >-
  async FW.csv(doc, options) // Reads a CSV Doc (documents stored in WILCO
  (admin/docs)
---

# FW.csv

This function fetches the document passed in parameter and maps it to an array of objects (within a promise). The document can be referenced by its ID or its name.



{% hint style="info" %}
Note that it cannot be the ref (plugin-componentXid) because the doc can be overrided for each airline. The name only is sufficient. NB: the name **is** the component XID
{% endhint %}

The result is an array of object. Each object represents each line. Each line is a key/value. The key is by default the first line element. And the value is the cell of the current line.

for example,

| A    | B      |
| ---- | ------ |
| TOTO | AZERTY |
| TATA | QUERTY |

would be represented like this:

```javascript
const docByName = await FW.csv(65257)
//docByName= 
[
{A:'TOTO', B:'AZERTY'},
{A:'TATA', B:'QUERTY'},
]
```

```javascript
//reads a doc which separator is ;
const docByName = await FW.csv('THE_DOC_NAME', {delimiter:';'});
//reads a doc which separator is tab
const docById = await FW.csv(2375267, {delimiter:'\t'});
```

The method does its best to find the correct delimiter, but it is always better to pass it explicitely as above

More generally, the options is an object that can take those properties:

* **output**: The format to be converted to. "json" (default) -- convert csv to json. "csv" -- convert csv to csv row array. "line" -- convert csv to csv line string
* **delimiter**: delimiter used for separating columns. Use "auto" if delimiter is unknown in advance, in this case, delimiter will be auto-detected (by best attempt). Use an array to give a list of potential delimiters e.g. \[",","|","$"]. default: ","
* **quote**: If a column contains delimiter, it is able to use quote character to surround the column content. e.g. "hello, world" won't be split into two columns while parsing. Set to "off" will ignore all quotes. default: " (double quote)
* **trim**: Indicate if parser trim off spaces surrounding column content. e.g. " content " will be trimmed to "content". Default: true
* **checkType**: This parameter turns on and off whether check field type. Default is false. (The default is `true` if version < 1.1.4)
* **ignoreEmpty**: Ignore the empty value in CSV columns. If a column value is not given, set this to true to skip them. Default: false.
* **noheader**:Indicating csv data has no header row and first row is data row. Default is false. See [header row](https://github.com/Keyang/node-csvtojson#header-row)
* **headers**: An array to specify the headers of CSV data. If --noheader is false, this value will override CSV header row. Default: null. Example: \["my field","name"]. See [header row](https://github.com/Keyang/node-csvtojson#header-row)
* **flatKeys**: Don't interpret dots (.) and square brackets in header fields as nested object or array identifiers at all (treat them like regular characters for JSON field identifiers). Default: false.
* **maxRowLength**: the max character a csv row could have. 0 means infinite. If max number exceeded, parser will emit "error" of "row\_exceed". if a possibly corrupted csv data provided, give it a number like 65535 so the parser won't consume memory. default: 0
* **checkColumn**: whether check column number of a row is the same as headers. If column number mismatched headers number, an error of "mismatched\_column" will be emitted.. default: false
* **eol**: End of line character. If omitted, parser will attempt to retrieve it from the first chunks of CSV data.
* **escape**: escape character used in quoted column. Default is double quote (") according to RFC4108. Change to back slash (\\) or other chars for your own case.
* **includeColumns**: This parameter instructs the parser to include only those columns as specified by the regular expression. Example: /(name|age)/ will parse and include columns whose header contains "name" or "age"
* **ignoreColumns**: This parameter instructs the parser to ignore columns as specified by the regular expression. Example: /(name|age)/ will ignore columns whose header contains "name" or "age"
* **colParser**: Allows override parsing logic for a specific column. It accepts a JSON object with fields like: `headName: <String | Function | ColParser>` . e.g. {field1:'number'} will use built-in number parser to convert value of the `field1` column to number. For more information See [details below](https://github.com/Keyang/node-csvtojson#column-parser)
* **alwaysSplitAtEOL**: Always interpret each line (as defined by `eol` like `\n`) as a row. This will prevent `eol` characters from being used within a row (even inside a quoted field). Default is false. Change to true if you are confident no inline line breaks (like line break in a cell which has multi line text).
* **nullObject**: How to parse if a csv cell contains "null". Default false will keep "null" as string. Change to true if a null object is needed.
* **downstreamFormat**: Option to set what JSON array format is needed by downstream. "line" is also called ndjson format. This format will write lines of JSON (without square brackets and commas) to downstream. "array" will write complete JSON array string to downstream (suitable for file writable stream etc). Default "line"
* **needEmitAll**: Parser will build JSON result is `.then` is called (or await is used). If this is not desired, set this to false. Default is true. All parameters can be used in Command Line tool.



More information here: [https://github.com/Keyang/node-csvtojson#parameters](https://github.com/Keyang/node-csvtojson#parameters)

