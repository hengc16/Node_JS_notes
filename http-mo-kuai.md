# Http模块

### 介绍

http模块负责帮你创建编写服务器的模块

post和get请求方式的区别是，get把请求内容放在URL后面，但是URL长度有限制。而post是以表单的形势，适合要输入密码之类的，因为不在URL中显示，所以比较安全。

### 创建

```javascript
let http = requrie('http')

let server = http.createServer()
```

### 服务器责任

* 提供对数据的服务
  * 发请求
  * 接收请求
  * 处理请求
  * 给response

1. 绑定端口号，启动服务器：
   1. server.listen\(3000\)
2. 请求（request\),当用户请求发过来，会自动触发服务器的request事件，然后执行回调函数。
   1. 回调函数有个参数
      1. request：获取客户端的请求消息，如请求路径request.url
         1. 在服务器发送数据默认是utf-8，但是浏览器在不知道服务器响应内容编码时，会自动按当前操作系统的默认编码去解析。
         2. 解决办法是加res.setHeader\('Content-Type', 'text/plain; charset= utf-8'\) 
      2. response: 发响应消息给客户端
         1. response.write\(\) write 可以使用多次，但是一定要使用end来结束响应，否则会一直停在等待状态。

```javascript
server.on('request' , function(request,response){
    res.setHeader('Content-Type', 'text/plain; charset= utf-8') 
    console.log("收到请求,请求路径为" + request.url)
    response.write("hello")
    resposne.write("world")
    response.end()
})
```

![](.gitbook/assets/image%20%282%29.png)

![](.gitbook/assets/image%20%283%29.png)

#### 通过不同的url路径给出同的响应

* /login  显示登陆
* /register 显示注册
* / 显示主页
* other  404 not found 

![](.gitbook/assets/image%20%284%29.png)

![](.gitbook/assets/image%20%285%29.png)

```javascript
let http = require('http')
let server = http.createServer()

server.listen(3000, function(){
    console.log("server up, visit localhost/3000")
})

server.on('request' , function(request,response){
    console.log("收到请求,请求路径为" + request.url)

    if(request.url == "/"){
        response.end('index page')
    }else if(request.url == "/register"){
        response.end("register page")
    }else if(request.url == "/login"){
        response.end("login page")
    }else{
        response.end("404 not found")
    }

})
```

### 如果想响应json

* res.end\(\)内只能响应二进制或者字符串。
* 数组，数字，boolean，object都不可以。

```javascript
    }else if(request.url == "/products"){
        let products = [
            {
                name : 'apple',
                price: 1
            },
            {
                name : 'grape',
                price: 5
            },
            {
                name : 'watermelon',
                price: 3
            }
        ]
        response.end(JSON.stringify(products))
    }
```

![](.gitbook/assets/image%20%286%29.png)



