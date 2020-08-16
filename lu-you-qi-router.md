# 路由器router

### 介绍：

* Router是一个完整的中间件和路由系统，也可以看做是一个小型app对象

### 为什么使用router：

* 随着业务的增加，server里面要增加get url 路由
* 所以我们需要路由器去管理路由

### Router的使用：

 `var router = express.Router();`

或  `const{Router} = require('express')` 

```jsx
let router = new Router();

router.get('/login', (res, req) => {...})

model.exports = router
```

在server main文件里如何引用

```jsx
const UIRouter = require('./router/UIRouter')
const db = require('./db/db')

db(() => {
 // 使用ui router
 app.use(UIRouter)
 
 app.listen(3000,(err) => {
  if(!err) console.log('success')
  else console.log(err)
 })
}, (err)=>{})
```

