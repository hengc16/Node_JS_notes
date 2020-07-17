# url模块&重定向

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
// 一次end对应一次响应，响应结束拿请求也结束了。后面对res的请求就没了
    res.end(JSON.stringify(parseObj.query))
}
```

### 如何让客户端重定向：

* 状态码设置为302，可以临时重定向
  * statusCode
* 在响应头中通过location来告诉client往哪里重定向
  * setHeader\(\)

如果客户端发现响应状态码是302，就好自动去header里面找location实现客户端自动跳转。

```javascript
res.statusCode = 302;
res.setHeader('Location', '/');
//记得结束响应
res.end();
```

![](.gitbook/assets/image%20%2812%29.png)

