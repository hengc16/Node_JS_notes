# 封装ajax

### 普通封装

```javascript
function get(url, callback) {
    var oReq = new XMLHttpRequest()
    //当请求加载成功后， 调用指定函数
    oReq.onload = function() {
        //我们需要通过回调函数来得到这个异步结果。
        callback(oReq.responseText)
    }
    oReq.open("get", url, true)
    oReq.send()
}
//封装到get函数里，并通过callback 函数来拿到异步操作的result
get('data.json', function(data) {
    console.log(data)
}
```

### 用promise封装

```javascript
function get(url) {
    return new Promise(function(resolve, reject) {
        var oReq = new XMLHttpRequest()
        //当请求加载成功后， 调用指定函数
        oReq.onload = function() {
            //我们需要通过resolve来得到这个异步结果。
            resolve(oReq.responseText)
        }
        oReq.onerror = function(err){
            reject(err)
        }
        oReq.open("get", url, true)
        oReq.send()
    })
}
```



