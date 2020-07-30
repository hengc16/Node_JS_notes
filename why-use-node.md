# why use node

{% embed url="https://www.joyent.com/blog/node-js-on-the-road-cincinnati-reid-burke" %}

* speaker from yahoo.



### why node?

* trusted, understood and test over years
  * it was first used as devs tools, then yahoo itself.

### where we used node?

* hosted apps
  * homepage & my yahoo
    * server side rendering, replace legacy code.
  * flickr
    * photo page is generate by node
  * advertising
  * video beacon 
* CI/CD
  * CI/CD stands for continuous integration and continuous delivery.
  * It is an agile methodology to help dev team to change the code and deliver the code more frequently and reliably. 
  * used jenkins for CI part, 
    * facing problem like having one jenkins to power all the yahoo's project is not going to work. 
    * performance is not good.
  * yahoo is current use node interface on top of jenkins.
    * so people only need to know javascript to add more plugin or node module to the system,
    *  no need to learn java, test with java ide, try on linux, know jenkins API ,etc. 
    * CI builds on your own machine 
* dev tools:
  * Cross platform 
  * easy installation 
  * internal registry
    * ynmp-&gt; extension of npm.

### problems

* out of memory.
  * memory leak are hard to debug. 
* errors
  * unexpected error happens 
    * what we do at yahoo
      * wrap the error.
        * if is the user's fault\(invalid input\),  wrapped error \( show something more descriptive \)
        * if sde's fault, unwrapped error \(show 500, its our fault\).
        * handler crashes if unrecoverable.

```text
if(err.isWrapped) {
    _reply(err.statusCode, err.message);
    log(err.source); 
}else {
    _reply(500); //internal server error
    log(err);
}
```

### future of node:

* node makes things easy 
* hard to mess up things 
* clean code 
* make engineer happy



