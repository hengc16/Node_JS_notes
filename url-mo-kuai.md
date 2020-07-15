# url模块

* 可以通过require\('url'\) 来引入包
* 通过url.parse\(\)这个方法来解析url 到obj
* 通过解析后的obj来筛选里面的pathname 或query

```javascript
var url = require('url')
var obj = url.parse('/pathlun?name=jack&message=helloworld',true)
console.log(obj)
console.log(obj.pathname)
console.log(obj.query)
```

这里的true是表示把字符串转换为对象,通过query属性来访问。

```javascript
else if(pathname === '/comment') {
    res.end(JSON.stringify(parseObj.query))
}
```

