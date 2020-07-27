# body-parser

* 如果urlencoded为false， bodyparse不会帮我们整理数据
* 如果为true， 就会帮我们整合数据
* input

![](.gitbook/assets/image%20%2821%29.png)

* output

![](.gitbook/assets/image%20%2819%29.png)

### req.body vs req.params



`req.body` is used to access actual form data that you 'posted'.

`req.params` is used for route parameters, in your case `userId` which is passed in the parameters:

```text
router.post("/user/:userId", function(req, res) {
  let thisUserId = req.params.userId;
}
```

