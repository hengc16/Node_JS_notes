# 基本路由（router）



![](.gitbook/assets/image%20%2814%29.png)

### 路由：

* 请求方法
* 请求路径
* 请求函数

### 访问静态资源

```javascript
//当以/public/开头的时候，去./public/目录里去找相对应的资源
app.use('/public', express.static('./public'))
//当省略第一个参数的时候，则可以通过省略/public的方法，直接按文件路径访问public里面的资源
app.use(express.static('./public'));

```



