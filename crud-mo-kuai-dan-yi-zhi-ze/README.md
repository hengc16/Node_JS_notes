# CRUD小项目

### 起步

* 初始化
* 将app.js 作为入口模块
* 将router.js 作为路由模块。

### 路由设计

| 请求 | 请求路径 | get参数 | post参数 | 备注 |
| :--- | :--- | :--- | :--- | :--- |
| GET | /students |  |  | 渲染主页 |
| GET | /students/new |  |  | 渲染添加学生主页 |
| POST | /students/new |  | name,age,gender,gpa | 处理添加请求 |
| GET | /student/edit | id |  | 渲染编辑页面 |
| POST | /student/edit |  | id,name,age,gender,gpa | 处理编辑请求 |
| GET | /students/delete | id |  | 处理删除请求 |
|  |  |  |  |  |

### express的路由容器：

```javascript
var router = express.outer();
router.ger('/students', function(req,res){});
module.exports = router;
```

在app文件里，将路由容器挂载到app上

```javascript
var router = requrie('./router');
app.use(router);
```



