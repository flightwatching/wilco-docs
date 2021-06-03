# draw a serie \(curve\)

`drawSerie(name, data, opts)`

* `name`: the name of the serie. Has to be unique in the chart. It will identify the curve among others.
* `data`: an array of {x, y} elements, where x is a date and y a number
* `opts`: it is an object that defines customizations:
  * `autoScaleX`: The X axis is recomputed to match the data.
  * `autoScaleY`: The Y axis is recomputed to match the data.
  * `color`: the color as web color or RGB hex
  * `width`: the width
  * `opacity`: the opacity of the curve \(0..1\)
  * `type`: can be `AREA` or `LINE`. If not defined, then it is a line.

#### 

