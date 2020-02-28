# MAIL\_TEMPLATE

Contains a HTML piece of code that will be appended to all the emails that are sent by the tool. Can be a signature, for instance. There are some variables that are injected that you can use with groovy syntax.

* id: the ID of the origin event that trigged the IFT. can be null
* source: A structure representing the IFT with 3 strings: 
  * kind: type of IFT
  * formula: the formula that trigged
  * editHRef: the HRef to edit the IFT
* msg: the EventV3IO that originated the message. Can be null. 

```markup
<br> <br> Check ${msg?.sumUp} details <a href="${url}">here</a> 
<br> <br> <em>Health Monitoring by Flightwatching</em>
```

