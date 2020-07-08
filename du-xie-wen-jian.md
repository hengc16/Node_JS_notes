# 读写文件

### 介绍

* browser中的js是不支持读写文件的。
* 在node.js中加入了相应的模块，可以支持读写文件

### 读取操作

* 使用require 方法加载 fs 核心模块

```javascript
let fs = require('fs')
```

* 读取文件
  * 第一个参数为文件路径
  * 第二个参数为回调函数
    * 成功
      * data：数据
      * error：null
    * 失败：
      * data: undefined
      * error：错误对象

```javascript
fs.readFile('./data/hello.txt', function (error, data) {
  if(error){
   console.log("fail") 
  }else{
    console.log(data.toString())  
  }
})
```

toString\(\) 是为了把16进制的file数据转成人类可读的数据。

### 写入操作

* 第一个参数：文件路径
* 第二个参数：文件内容
* 第三个参数：回调函数

```javascript
let fs = require('fs')
fs.writeFile('test.md', "ni hao", function(error){
    if(error){
        console.log(error.message);
    }else{
        console.log("success");
    }
})
```

