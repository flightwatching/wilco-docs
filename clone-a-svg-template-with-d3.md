# Clone a SVG template with D3

{% embed url="https://bl.ocks.org/mbostock/9360565" %}



```javascript
var itemTemplate = d3.select(".item").remove().node();

var formatCost = d3.format("$,.2f"),
    formatCount = d3.format(",d");

d3.tsv("items.tsv", type, function(error, items) {
  var item = d3.select("#item-table tbody").selectAll(".item")
        .data(items)
      .enter().append(function() { return itemTemplate.cloneNode(true); });

  item.select(".name").text(function(d) { return d.name; });
  item.select(".cost").text(function(d) { return formatCost(d.cost); });
  item.select(".count").text(function(d) { return formatCount(d.count); });
});

function type(d) {
  d.cost = +d.cost;
  d.count = +d.count;
  return d;
}
```

\
