# 匿名函数

```javascript
(function(){
    var a = 1 + 2
})();
```

user has no global access to this function. =》 more safety 

### 匿名函数 + 异步处理

```javascript
(async() => {
    let client = await MongoClient.connect(dbURL, {useNewUrlParse: true, useUnifiedTopology: true});
    console.log('Sucessfully connected to ', client.s.options.dbName);
    client.close();
})()
```

* 比promise更高级的用法，用async和await
* client会等待（await）异步函数connect 调用结束， 拿到client 再继续往下执行。
* await 用在异步函数调用前面，并且await需要被async包裹住，不能单独拿来用。



