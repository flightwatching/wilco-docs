# draw circles

All the dots/circles of the graph are set thru this function. You cannot name the groups as for the curves.

`drawCircles(dots, opts)`

* `dots`: a array of `dot` structures like this:
  * `id`: a unique ID for the dot. It is optional. `id` is useful for transitions, recalls to ensure each circle is affected to the same business dot.
  * `x`: the x position of the dot \(date\)
  * `y`: the y position of the dot \(date\)
  * `title`: the tooltip of the dot \(text\)
  * `color`: the color of the dot \(string\). can also be a function where the parameter is the `dot`. the return should be a web color or a hex value
  * `radius`: the size of the circle of the dot \(string\). can also be a function where the parameter is the `dot`. the return should be a number
  * `opacity`: the opacity of the circle of the dot \(string\). can also be a function where the parameter is the `dot`. the return should be a number between 0 and 1
* `opts`: the default values if they are not specified in each dot.
  * `autoScaleX`: The X axis is recomputed to match the data.
  * `autoScaleY`: The Y axis is recomputed to match the data.
  * `color`: the color of the dot \(string\). can also be a function where the parameter is the `dot`. the return should be a web color or a hex value
  * `radius`: the size of the circle of the dot \(string\). can also be a function where the parameter is the `dot`. the return should be a number
  * `opacity`: the opacity of the circle of the dot \(string\). can also be a function where the parameter is the `dot`. the return should be a number between 0 and 1

