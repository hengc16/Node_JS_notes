# Express

写个hello——world

```javascript
//引包
var express = require('express');


//2. 创建你的server
//也就是原来的http.createServer
var app = express();

//当服务器收到get请求/的时候，响应回调函数
app.get('/', function(req, res){
    res.send('hello world');
});

//监听端口
app.listen(3000, function(){
    console.log('app is running at localhost 3000');
});

```

### 多路径

* 原来需要一个个判断的路径
* 在express里不需要

```javascript
//引包
var express = require('express');


//2. 创建你的server
//也就是原来的http.createServer
var app = express();

//当服务器收到get请求/的时候，响应回调函数
app.get('/', function(req, res){
    res.send('hello world');
});
app.get('/login', function(req, res){
    res.send('hello world');
});
app.get('/404', function(req, res){
    res.send('hello world');
});
app.get('/home', function(req, res){
    res.send('hello world');
});
//监听端口
app.listen(3000, function(){
    console.log('app is running at localhost 3000');
});
```

### 公开指定目录：

* 用户可以通过/public/资源 来访问公开资源

```javascript
app.use('/public/', express.static('./public/'))
```

### 获取查询字符串：

* 在express中，可以直接用req.query来或许查询字符串参数

```javascript
app.get('/about', function(req, res) {
    let tempQuery = req.query;
    console.log(tempQuery);
    res.send('你好');
});
//如果url是 /about?foo=bar
//那query 就会是一个 {foo : 'bar'} 的一个object
```

### 重定向：

```javascript
app.get('/comments', function(req, res){
    let comment = req.query;
    comment.date = '2020-7-19 9:28:51';
    comments.unshift(comment);
    res.redirect('/');
})
//注意 req.query只能拿get请求参数
```

### 

