互联网中的设备是如何进行通信的？

TCP/IP参考模型

这个模型有5层：物理层、数据链路层、网络层、传输层和应用层。

Physical layer

物理层的作用是将比特从一台机器传输传输到另一台机器。

Link layer

数据链路层

比如以太网(Ethernet)和802.11都是数据链路层的协议。

Application layer

应用层

This is the layer in which all high level protocols, such as HTTP, SSH, FTP, WebSocket, operate.

Transport layer

传输层

![](../assets/tcp-header.png)

如果把IP地址比作一间房子，端口就是出入这间房子的门。

端口通过端口号来标记，端口号是整数。

通过上图可以得知，端口号的范围为0到2的16次方减一之间的任意整数。

Internet layer

网络层

传输控制协议

The Transmission Control Protocol(TCP) is   

Transmission Control Protocol accepts data from a data stream,

每个分层中，都会对所发送的数据附加一个首部。

Every layer will encapsulate the appropriate header.

![](../assets/tcpip-header.png)

TCP three-way handshake

Sequence number(32 bits)

- If SYN flag is set (1), then this 

- SYN(1 bit): Synchronize sequence number. Only the first packet sent from each end should have this flag set.

在传输层中也有类似于地址的概念，那就是端口号。

端口号用来识别同一台计算机中进行通信的不同应用程序，因此，它也被称为程序地址。

TCP是面向连接的，在实际发送数据之前，客户端和服务器需要建立起一个TCP连接。

请求在"三次握手"的第三次"握手"就发送出去了

为什么降低HTTP/TCP延时是一个非常重要的议题?

因为它决定了我们在互联网中访问某一站点时，该站点所包含的相关资源全部加载完成的时间。

如果每个事务都需要(串行地建立)一条新的连接，那么连接时延和慢启动时延就会叠加起来。

有几种现存和新兴的方法可以提高HTTP的连接性能。

浏览器可以先完整地请求原始的HTML页面，然后

HTTP允许客户端打开多条连接，并行地执行多个HTTP事务，每个事务都有自己的TCP连接。