# 中间件middleware

### 概念：

* 本质上就是一个函数，包含3个参数，request，response，next

### 作用：

* 执行代码
* 修改请求和响应对象
* 终结请求
* 调用堆栈中的下一个中间件或路由

### 分类：

![](.gitbook/assets/image%20%2828%29.png)

应用于全局的是应用级中间件，----所有请求的第一扇门。

如果有响应，就不会看后面的了。

next\(\)算是放行

### 函数定义中间件

使用函数定义， 把防盗链写在demo函数里， app.get时候调用。

![](.gitbook/assets/image%20%2823%29.png)

### 第三方中间件：

body-parser等

### 内置中间件：

* app.use\(express.static\('public'\)\)

使用内置中间件去暴露静态资源

`app.use(express.static(__dirname + '/public'))`

把public folder下的静态资源都交出去了， 不需要路由也可以用/来匹配public下的html img 等

注意必须通过.html 来访问，不带后缀 访问不到。



