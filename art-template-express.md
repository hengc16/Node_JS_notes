# 配置服务端模板引擎

### 安装：

```javascript
npm install --save art-template
npm install --save express-art-template
```

### Examples:

```javascript
var express = require('express');
var app = express();

// view engine setup  主要是这句话配置使用
//第一个参数，表示，当渲染以.art结尾的文件时，使用art-template模板引擎渲染
app.engine('art', require('express-art-template'));
//加不加无所谓
app.set('view', {
    debug: process.env.NODE_ENV !== 'production'
});
app.set('views', path.join(__dirname, 'views'));
app.set('view engine', 'art');

// routes
app.get('/', function (req, res) {
    res.render('index.art', {
        user: {
            name: 'aui',
            tags: ['art', 'template', 'nodejs']
        }
    });
});
```

* 虽然没有require art-template,但是我们还是要npm art-template, 因为express-art-template依赖于art-template.
* Express 为response响应对象提供了个方法：render
  * render方法默认是不可用的，除非配置了模板引擎
  * res.render\('html.模板名', {模板数据}\)
  * 第一个参数不能写路径，默认去项目里的views目录找模板文件
  * 也就是说express规定开发人员把视图文件放views目录里
* 如果想要修改views目录
  * app.set\('views', 替换路径）

