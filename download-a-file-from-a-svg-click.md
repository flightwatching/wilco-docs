# Download a file from a SVG click

See [https://gist.github.com/danallison/3ec9d5314788b337b682](https://gist.github.com/danallison/3ec9d5314788b337b682)

```javascript
      _anim.on('click', (d)=>{
        const a = window.document.createElement('a');
        a.download = `${d.ift.code}_${EVT.reg}.txt`;
        a.href = "data:application/octet-stream," + encodeURIComponent(getCD(d));
        a.dataset.downloadurl = ['text/plain', a.download, a.href].join(':');
        a.style.display = "none";
        window.document.body.appendChild(a);
        a.click();
        window.document.body.removeChild(a);
      });
```
