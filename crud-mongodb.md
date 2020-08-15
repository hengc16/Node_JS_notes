# CRUD mongodb

设计schema 并转成model，拿到模型对象

### 增加数据

```javascript
//增加
let admin = new User({
    username: 'admin',
    password: "123456",
    email: "admin@admin.com"
})
//实例一个User，并通过.save 来进行添加
admin.save(function(err, res){
    if(err) {
        console.log('save fail')
    }else{
        console.log('saved')
        console.log(res);
    }
})
```

### 查询数据

```javascript
//查询集合里的所有对象，返回一个数组of object
User.find(function(err, res){
    if(err){
        console.log('find fail')
    }else{
        console.log(res)
    }
})

//按条件查询 多个
User.find({username:'admin'},function(err, res){
    if(err){
        console.log('find fail')
    }else{
        console.log(res)
    }
})

//按条件查询单个（返回第一个符合条件的)
User.findOne({
    username: 'admin',
    password: '123456'
}, function(err, res){
    if(err){
        console.log('find fail')
    }else{
        console.log(res)
    }
})

//拿所有，但是只是显示selected
let res = User.find({}, 'username')
console.log(res);
```

### 删除数据：

```javascript
//按条件删除全部
User.deleteMany({
    username: 'admin2'
},function(err, res){
    if(err){
        console.log('remove fail')
    }else{
        console.log(res)
    }
})

//按条件删除一个
User.deleteOne({
    username:'admin2',
    password:'123456'
},function(err, res){
    if(err){
        console.log('remove fail')
    }else{
        console.log(res)
    }
})
```

### 更新数据：

```javascript
//更新指定数据
User.findByIdAndUpdate('5f1dcd26912cc108ac5a015a',{password: '1234567'},function(err, res){
    if(err){
        console.log('update fail')
    }else{
        console.log(res)
    }
})
//更新一个，第一个参数是根据属性找到document， 第二参数是更新那个document里的相应属性
let res = await Course.updateOne( {courseNumber: 'cs701'}, 
                                    {courseName: 'Rich Internet APP Development'});

```

