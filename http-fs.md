# Http-fs

* 结合fs来读取文件数据并通过http去发送
* Content-Type 可以网上搜对应commons
  * [https://tool.oschina.net/commons](https://tool.oschina.net/commons)
* 不同资源类型的content-type不同
  * jpg =&gt; image/jpeg
  * png =&gt; image/png
  * txt =&gt; text/plain
  * html =&gt; text/html
  * css =&gt;text/css
  * js =&gt; application/x-javascript

```javascript
var http = require('http');
var fs = require('fs');

const server = http.createServer();

server.on('request', function(req, res){
    let url = req.url;
    if(url === '/') {
        fs.readFile('./resource/index.html', function(err, data){
            if(err){
                res.setHeader('Content-Type','text/plain; charset = utf-8');
                res.end('读取文件失败');
            }else{
                res.setHeader('Content-Type','text/html; charset = utf-8');
                // data是默认二进制数据，需要转换
                //但是res.end 支持2钟数据类型，2进制和字符串，所以不用转
                res.end(data);
            }
        })
    }
})
```

