# 获取post表单请求体

* express中没有内置post请求体api。
* 需要通过第三方插件middlewire 来完成

### 安装：

```text
npm install body-parser
```

### 使用：

```javascript
var express = require('express')
//引包
var bodyParser = require('body-parser')

var app = express()

// 配置body-parser
//只有加入这个配置，则在req请求对象上会多出来一个属性：body
// 也就是说可以通过 req.body来获取表单 post 请求体
app.use(bodyParser.urlencoded({ extended: false }))

// parse application/json
app.use(bodyParser.json())

app.use(function (req, res) {
  res.setHeader('Content-Type', 'text/plain')
  res.write('you posted:\n')
  //可以通过req.body来获取数据
  res.end(JSON.stringify(req.body, null, 2))
})
```



