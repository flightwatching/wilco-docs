# Set the title of the graph

The title is positionned in the middle of the graph and right on the margin of the chart \([creation of the graph](creation-of-the-graph.md)\)

You can overide some settings with the `opts` parameter

`graph.title(title, opts)`

* `title`: A string that will be displayed as the title of the graph
* `opts`: 
  * size: the font-size for the text
  * any attribute in [https://developer.mozilla.org/en-US/docs/Web/SVG/Element/text](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/text)

```javascript
  myGraph.title("Reverser 1", {
    size: "0.3em",
    fill: "red",
    y: 10
  });
```



