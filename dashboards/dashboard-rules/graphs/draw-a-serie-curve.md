# draw a serie (curve)

`drawSerie(name, data, opts)`

* `name`: the name of the serie. Has to be unique in the chart. It will identify the curve among others.
* `data`: an array of {x, y} elements, where x is a date and y a number
* `opts`: it is an object that defines customizations:
  * `autoScaleX`: The X axis is recomputed to match the data.
  * `autoScaleY`: The Y axis is recomputed to match the data.
  * `color`: the color as web color or RGB hex
  * `width`: the width
  * `opacity`: the opacity of the curve (0..1)
  * `type`: can be `AREA` or `LINE`. If not defined, then it is a line.
  * style: is an object where you can add any attribute to fill the css style of the serie
  * svg: is an object where you can add a path attribute of the serie (eg: dash...)

####
