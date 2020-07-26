# NPM

* 用来下来包的
* --save 是用来加dependencies到package.json
* 不加--save 会发现package.json文件中不会加入包的信息
* package.json 就像是产品的说明书，包描述文件。
* 可以通过npm init 来通过向导来创建project
* 只要有package.json 在这个project里，我们就可以通过npm install来下载所以依赖的包

### 常用命令：

* npm init
  * npm init -y 跳过向导，快速生成
* npm install
* npm install 包名
  * 只下载
* npm install --save 包名
  * 下载保持依赖项\(package.json 的dependencies）
* npm uninstall 包名
  * npm un 包名  （简写）
  * 只删除，如果有dependencies会依然保存
* npm uninstall --save 包名
  * npm un -s 包名 \(简写\)
  * 删除+dependencies一起删
* npm help 
  * 不懂就问
* npm 命令 --help 
  * 具体不知道

### package.json 和package-lock.json

* npm5以前是没有package-lock.json这个文件的
* 当前安装包的时候，npm都会生成或更新package-lock.json这个文件
* 5以后也不需要加--save 他会自动生成dependencies
  * package-lock.json 会保存node\_modules中所以包的信息，（版本，下载地址）
  * 提高下载速度
* lock是为了锁定版本的











