# 统一管理静态资源

* 将公共资源放在public里。

![](.gitbook/assets/image%20%2811%29.png)

* 如果html里带外链（href）资源，服务器会自动对资源发起请求
* 在服务端中，文件路径就不要去写相对路径了
* 所以资源都通过url来获取
* 可以将请求路径统一写为/public/xxx 来统一管理
* 把所以资源都想成url去拿资源。

```javascript
if(url.indexOf('/public') === 0) {
//如果请求是以/public开头的， 则自动认为是获取public文件夹中的某个资源
    fs.readFile('.' + url, function(err, data) {
        if(err){
            return res.end('404 not found');
        }
        res.end(data);
    }
}
```



