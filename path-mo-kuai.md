# path 模块

### 介绍

* 因为router 和app 所需要的路径是绝对路径，开发人员在无法是用 ../， 为了解决更方便的url跳转。
* 我们可以使用path

### 使用path

```jsx
//内置模块， 直接引用
let path = require('path')

router.get('/login', (req, res) => {
//这里path.resolve的第一个参数是 起始点， 第二个参数是规则。
    let url = path.resolve(__dirname, '../public/login');
    res.sendFile(url);
}
```

