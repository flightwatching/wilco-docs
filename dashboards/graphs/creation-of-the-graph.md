# creation of the graph

`const graph = new WILCO.Graph(container, options)`

* `container`: a d3 `<g>` element that will host the graph \(ex: `my_anim.go()`\). A sub container will be created within it and translated accordingly
* `options`: it is an object that defines customizations:
  * `width`: the width of the graph \(number\). If not passed, then the bounding box of the container is used
  * `height`: the height of the graph \(number\) If not passed, then the bounding box of the container is used
  * `xScale`: a d3 scale: `d3.time.scale()` to force the X span
  * `yScale`: a d3 scale: `d3.scale` to force the Y span
  * `margin`: a structure like `margin: {left:0, top:0, bottom:10,right:0}` to set the margins of the chart. By default, it is `margin: {left:30, top:30, bottom:30,right:30}`,
  * `axis`: do you want to display the axis. See below for options: `axis: { showX:{grid:true}, showY:false}`

> Please note that the bounding box of a container \(`g`\) is the bounding box of its content. It means that if you define the container as an empty group, it will have x, y, height and width set to 0. To have a correct bounding box, we suggest you add a `<rect>` in it so that the bounding box is the rect properties

Here is the definition of the axis object:

* `grid`: a boolean to display or not the grid
* `ticks`: the count of ticks
* `size`: the size of the text displayed for each tick

example:

```javascript
{
  margin: {left:0, top:10, bottom:0,right:0},
  axis: { showX:{ticks:6, grid:true, size: '0em'}, showY:false},
  xScale: d3.time.scale().domain(this.xExtent),
  yScale: d3.scale.linear().domain([0,6])
}
```

#### 

