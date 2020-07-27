# Promise

### 什么是promise

![](.gitbook/assets/image%20%2822%29.png)

* 实现异步功能
* 同步代码实现异步操作
* 像是个box 存放未来将要发生的事件
* promise本事不是异步的，往往

为什么实用promise

* avoid callback hell

### 步骤：

1. create an instance of promise 
2. create executor 
3. check status 
   1. case 1  resolve
   2. case 2 reject
4. get result

```javascript
const p = new Promise((res, rej) => {
    setTimeOut(() => {
        let num  = Math.random() * 100;
        console.log(num.toFixed(0));
        //check status
        if(num > 60) {
            res('ok');
        }else{
            rej('fail');
        }
    },1000);
})
p.then(
    result => {
        console.log('resolved');
        console.log(result);
    }
    err => {
    
        console.log('reject');
        console.log(err);
    }
)

```

在读多个文件时，因为读文件时异步操作，所以无法保证读文件的顺序。

为了保证文件读取顺序。

### \#1 callback函数嵌套

```javascript
var fs = require('fs')

fs.readFile('./data/a.txt', 'utf-8', function(err, data) {
    if(err) {
        console.log('error')
    }else{
        console.log(data)
    }
    fs.readFile('./data/a.txt', 'utf-8', function(err, data) {
    if(err) {
        console.log('error')
    }else{
        console.log(data)
        fs.readFile('./data/a.txt', 'utf-8', function(err, data) {
        if(err) {
            console.log('error')
        }else{
            console.log(data)
        })
    })
})
```

* 这种嵌套callback 也叫callback hell
* 这种方法是不可取的

### \#2 promise来规定异步操作顺序

```javascript
//在es6中新增个API Promise 构造函数
//创建Promise容器
//当容器一旦创建，就会执行里面的代码

let p1 = new promise ( fucntion(resolve, reject){
    fs.readFile('./data/a.txt', 'utf-8', function(err, data) {
        if(err) {
            //调用reject就相当于调用了then方法里的第二个参数函数
            reject(err)
        }else{
            //调用resolve就相当于调用了then方法里的第一个参数函数
            resolve(data)
        }
    })
})
//p1 就是promise的实例
//当p1 成功了， then 方法接收的function就是容器中的resolve函数。
p1.then(function(data){
    console.log(data)
},function(err){
    console.log('fail', err)
})
```

### 嵌套\(promise - chaining\)

```javascript
let p1 = new promise ( fucntion(resolve, reject){
    fs.readFile('./data/a.txt', 'utf-8', function(err, data) {
        if(err) {
            //调用reject就相当于调用了then方法里的第二个参数函数
            reject(err)
        }else{
            //调用resolve就相当于调用了then方法里的第一个参数函数
            resolve(data)
        }
    })
})


let p2 = new promise ( fucntion(resolve, reject){
    fs.readFile('./data/b.txt', 'utf-8', function(err, data) {
        if(err) {
            //调用reject就相当于调用了then方法里的第二个参数函数
            reject(err)
        }else{
            //调用resolve就相当于调用了then方法里的第一个参数函数
            resolve(data)
        }
    })
})

//p1 就是promise的实例
//当p1 成功了， then 方法接收的function就是容器中的resolve函数。
// 当前函数return的结果就可以在后面的then中的function收到
// 当你return 一个promise 对象的时候， 后面的then的第一个参数就会
// 是promise对象的resolved， 第二个参数就会使promise参数的rejected
p1.then(function(data){
    console.log(data)
    return p2
},function(err){
    console.log('fail', err)
})
.then(function(data){
    console.log(data)
}, function(err){
    console.log('fail', err)
})
```

