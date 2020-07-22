# 入口组件

### 职责：

* 启动服务 
* 做一些服务相关配置 
  * 模板引擎 
  * body-parser 解析表单 post请求体 
  * 提供静态服务 
* 挂载路由 
* 监听端口启动服务

```javascript
/*入口模块
职责：
    启动服务
    做一些服务相关配置
        模板引擎
        body-parser 解析表单 post请求体
        提供静态服务
    挂载路由
    监听端口启动服务
  */
var express = require('express');
var app = express();
var router = require('./router')


app.use('/node_modules/', express.static('./node_modules/'));
app.use('/public/', express.static('./public/'));
app.engine('html',require('express-art-template'))
//把路由容器挂载到app上
app.use(router);

// 监听端口启动服务
app.listen(3000, function(){
    console.log('running 3000');
});
```

