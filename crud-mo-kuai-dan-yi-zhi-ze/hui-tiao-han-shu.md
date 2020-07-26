# 回调函数

* 一般情况下，把函数作为参数的目的就是为了获取函数内部的异步操作结果
* 
setTimeout是js的异步操作函数

```javascript
console.log(1)
setTimeout(function(){
    console.log(2)
}, 1)

console.log(3) 
//output:  1 3 2 

```

错误示范

```javascript
function add(x,y) {
    console.log(1)
    setTimeout(function(){
        console.log(2)
        var res = x + y
        return res
    },1000)
    console.log(3)
}
consolo.log(add(10,20))
// output  1 3 undifined 2 
```

* 凡是需要得到一个函数内部异步操作的结果：
  * setTimeout
  * readFile
  * writeFile
  * ajax
* 这种情况必须通过：回调函数

```javascript
function add(x,y, callback){
    console.log(1)
    setTimeout(function(){
        var ret = x + y
        callback(ret)
    },1000)
}
add(10, 20, function(ret){
    console.log(ret);
})
```

* 通过回调函数拿到异步操作的结果。

