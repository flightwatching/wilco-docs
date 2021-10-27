# goto a page from a dashboard

```javascript
  hist_anim.go().style('cursor','pointer').on('click', ()=>{
      const url = `/wilco/#/${that.selectedApu.reg}/timeline`;
      WILCO.gotoPage(url, '_self'); // on the same page
      //WILCO.gotoPage(url, '_blank'); // in a new tab
  });
```
