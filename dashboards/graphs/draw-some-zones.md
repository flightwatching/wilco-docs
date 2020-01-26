# draw some zones

A zone helps to split the graph into zones. Zones are between 2 X values `drawZone(zones)`

* `zones` is an array of zone objects
  * `color`: the color of the zone as web color or RGB hex \(will be a little bit transparent\)
  * `size`: the font-size to apply on the `sn` text \(css size\)
  * `sn`: a short text that will be displayed vertically onto the border of the zone
  * `extent`: an array of 2 dates/numbers which are the X min and the X max values of the zone

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



