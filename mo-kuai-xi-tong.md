# 模块系统

### 模块系统

* 在Node中没有全局作用域的概念
* 在node中，只能通过require方法来加载执行多个js脚本文件
* require加载只能是执行其中的代码，文件与文件之间是模块作用域，所以不会污染。
  * 模块完全是封闭的，
  * 外部不能访问内部
  * 内部不能访问外部
* 模块提供了一个对象exports来实现模块模块之间的通信
* exports默认为空对象
* 可以将需要外部访问的成员手动挂载到‘exports’这个接口对象中
* 谁require这个模块，谁就可以得到‘exports’这接口对象

### 核心模块：

* 由Node.js 提供的模块，如
  * fs 文件操作模块
  * http 网络服务构建模块
  * os 操作系统模块
  * path 路径处理模块
  * 。。。。

### exports挂载和赋值

* exports的挂载可以在文件尾部直接.操作挂载
* exports = f\(\) 类似的赋值操作，需要调用module.exports = f\(\) 来完成

### 加载：

```javascript
var 自定义变量名 = require('模块')
```

* 2个作用：
  * 执行被加载的代码
  * 的到被加载模块中的exports接口对象

### 导出

* Node中是模块作用域，默认文件中所以的成员只有在当前文件模块有效
* 对应希望其他模块访问的成员，我们需要通过将其挂载到exports接口对象上实现公开
  * 导出多个成员: 挂载到exports对象
  * 导出单个成员：用module.exports做赋值操作，永远=最后一次赋值，覆盖之前的值。
* exports 是module.exports的一个引用
  * exports === module.exports     =&gt; true

