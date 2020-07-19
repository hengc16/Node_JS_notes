# Net模块

### Net

* net对应传输层，http对应应用层
* net用于创建TCP服务器和客户端
  * http用于创建http服务器和客户端
* net一般是和socket有关的api
  * http是http相关的api

### Tcp

* 建立一个tcp连接需要“3次握手”
  * 第一次握手：client发送syn 包到服务器，进入SYN\_SEND状态，等待server确认
  * 第二次：server 收到syn包，确认client的SYN，同时自己也发个SYN包，即SYN+ACK包，此时server进入SYN\_RECV状态
  * 第三次：client收到server发来的SYN\_ACK包，向server发送包ack，此包发送完毕，双方进入ESTABLISHED状态，完成3次握手。
* 握手中不传送数据，TCP连上后才开始传数据。
* 关闭TCP需要‘4次握手’确认关闭连接。



