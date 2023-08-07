# draw some zones

A zone helps to split the graph into zones. Zones are between 2 X values `drawZone(zones)`

* `zones` is an array of zone objects
  * `color`: the color of the zone as web color or RGB hex (will be a little bit transparent for the background, and full opacity for the text if any (`sn`) if it is a string. It can also be an object with background and text fields to separate those (`color:{text:'white', background:'none'}`)
  * `size`: the font-size to apply on the `sn` text (css size)
  * `sn`: a short text that will be displayed vertically onto the border of the zone
  * `extent`: an array of 2 dates/numbers which are the X min and the X max values of the zone
  * `opacity`: the opacity of the zone. By default, it is 0.2

```javascript
  const oooi = this.oooi = (OOOI.history().filter(e=>['ON', 'OFF'].includes(e[0])));
  const zones = this.oooi.reduce((zones, e)=>{
    zones.data.push( {
      id: e.date,
      color: (e[0]=="ON")?'grey':'steelblue',
      sn: '',
      size: "0.3em",
      extent: [+moment.utc(e.date), zones.currentDate]
    });
    zones.currentDate=+moment.utc(e.date);
    return zones;
  }, {currentDate: +this.timeDomain[1], data:[]}).data;

  mygraph.drawZone(zones);  

```

