# 通过node来连接mongodb

* 使用官方的mongodb包来操作
  *  [https://github.com/mongodb/node-mongodb-native](https://github.com/mongodb/node-mongodb-native)
* 使用第三方包mongoose来操作mongodb
  * [https://mongoosejs.com/](https://mongoosejs.com/)
  * api文档

```javascript
//引包
const mongoose = require('mongoose');
//连接数据库
mongoose.connect('mongodb://localhost:27017/test', {useNewUrlParser: true, useUnifiedTopology: true});
//创建一个模型， 
// mongodb是动态的， mongoose这个包可以让你的设计变的简单

const Cat = mongoose.model('Cat', { name: String });

//实例化一个cat
const kitty = new Cat({ name: 'Zildjian' });
//持久化保持kitty实例
kitty.save().then(() => console.log('meow'));
```

### schema 对集合的约束

```javascript
//引包
const mongoose = require('mongoose');
//设计表格式用的
const Schema = mongoose.Schema;

//连接数据库, 如果没有该数据库，会在你插入第一条数据时自动创建
mongoose.connect('mongodb://localhost:27017/test', {useNewUrlParser: true, useUnifiedTopology: true});
//创建一个模型， 
// mongodb是动态的， mongoose这个包可以让你的设计变的简单

//设计表格式
//规定好里面type
var blogSchema = new Schema({
    title: String,
    author: String,
    body: String,
    comments: [{body: String, data: Date}],
    date: {type: Date, default: Date.now},
    hidden: Boolean,
    meta: {
        votes: Number,
        favs: Number
    }

});

var userSchema = new Schema({
    username: {
        type: String,
        required: true
    },
    password: {
        type: String,
        required: true
    },
    email: {
        type: String,
        required : false
    }
})
//将文档结构发布为模型
//第一个参数：传入一个大写名词字符串来表示你的数据库名称
    //      mongoose会自动将大写名词转换为 小写负数 的集合名称
    //      例如这里的User会最终边为users 集合名称
//第二个参数： 结构Schema
//返回值: 模型对象
var User = mongoose.model('User', userSchema);

//当我们有了模型构造函数后，就可以使用这个构造函数对user集合做操作

```

