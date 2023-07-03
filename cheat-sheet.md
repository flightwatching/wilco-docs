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

**Select or selectAll**? how to modify children elements of a data() selection? see [here](https://bost.ocks.org/mike/nest/#conclusion)

## WILCO

groovy templates cheatsheet

[https://www.playframework.com/documentation/1.5.x/cheatsheet/templates](https://www.playframework.com/documentation/1.5.x/cheatsheet/templates)

## CHROME

Pour passer outre le CERT\_INVALID, notamment pour le développement: écrire "thisisunsafe" dans la fenetre de warning
