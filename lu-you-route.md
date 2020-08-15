# 路由route

路由里的request和response

### request对象

![](.gitbook/assets/image%20%2823%29.png)

* query的查询字符串参数是指 

         [www.abc.com/xxx?a=1&b=hello](http://www.abc.com/xxx?a=1&b=hello)  
         这里问号以后的部分，可以附带少量的参数。

         英文叫做querystring

* params 的参数路由是指 /amazon/:productId  

         这里可以通过req.params\(productId\)拿到id

         这里：productId 是占位符，从params里拿的时候要完全匹配。

* body 是用来拿post请求体，需要用bodyparser这个中间件来拿。
* get 是用来获取request对象里的key所对value。

![](.gitbook/assets/image%20%2825%29.png)

### Response对象

![](.gitbook/assets/image%20%2824%29.png)



