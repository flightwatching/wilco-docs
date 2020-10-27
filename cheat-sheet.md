# Cheat sheet

## SVG

center a text horiz and vertically

`text-anchor="middle" dominant-baseline="middle"`

## D3

change the cursor when hovering a SVG element

`this.go().style('cursor','pointer').on('click', ()=>{...})`

Set up a linear scale

`d3.scale.linear().domain([0,160])`

Set up a time scale

`d3.time.scale().domain([from, to])`

Setup a discrete output scale

`const crColors = d3.scale.threshold().domain([0,70,75,100]).range(['red', 'darkorange', 'yellow', 'grey']);`

## WILCO

## CHROME

Pour passer outre le CERT\_INVALID, notamment pour le développement: écrire "thisisunsafe" dans la fenetre de warning

