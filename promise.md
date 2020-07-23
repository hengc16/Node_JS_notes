# Promise

什么是promise

* 实现异步功能
* 同步代码实现异步操作
* 像是个box 存放未来将要发生的事件

为什么实用promise

* avoid callback hell

步骤：

1. create an instance of promise 
2. create excutor 
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

