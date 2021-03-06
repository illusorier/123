The **World Wide Web(WWW)**, also called **the Web** is an information space where documents and other web resources are identified by Uniform Resource Locators(URLs),

Web浏览器和Web服务器都是Web应用程序，它们通过相互发送报文来实现基本事务处理的。

现在使用的HTTP协议有几个版本。

版本0.9是HTTP协议的早期版本，是当今HTTP所拥有的请求及响应报文的鼻祖，但其协议要简单得多。

### 什么是HTTP报文？

HTTP报文是HTTP协议的一部分，它和TCP/IP其他层一样，会对所发送的数据附加一个首部。

HTTP messages are how data is exchanged between a server and a client.

There are two types of messages: *request* sent by the client to trigger an action on the server, and *responses*, the answer from the server.

HTTP messages are composed of textual information encoded in ASCII, and span over multiple lines.

In HTTP/1.1, and 

HTTP报文是在HTTP应用程序之间发送的数据块，这些数据块以一些文本形式的元信息（meta-information）开头，后面跟着可选的数据部分。

请求报文(request message)

响应报文(response message)

HTTP报文是简单的格式化数据块。

每条报文都包含一条来自客户端的请求，或者一条来自服务器的响应。

HTTP连接是HTTP报文传输的关键通道。

在任意时刻计算机都可以有几条TCP连接处于打开状态。

与建立TCP连接、以及传输请求和响应报文的时间相比，事务处理时间可能是很短的。

一般情况下，HTTP时延是由TCP网络时延构成的。

HTTP/1.1(以及HTTP/1.0的各种增强版本)允许HTTP设备

首部和方法配合工作，共同决定了客户端和服务器能做什么事情。

术语"Web服务器"可以用来表示Web服务器的软件，也可以用来表示提供Web页面的特定设备或计算机。

Socket又称"套接字"，应用程序通常通过"套接字"

实际的Web服务器会做些什么？

1. 建立连接

什么是防火墙？

A firewall is a network 

什么是反向代理？

Common uses for a reverse proxy server include:

- Loading balancing - 

### TCP 'Packet' Field

Connection-oriented means that, before any data can be transmitted, a reliable connection must be obtained and acknowledged.

TCP utilizes a number of flags, or 1-bit boolean fields, in its header to control the state of a connection.

Sequence Number (32Bits): Used for segmentation of application data into TCP segments and reassembling them on the other side.

Initial Sequence Number (什么是ISN?)

ISN refers to the unique 32-bit sequence number assigned to each new connection on a TCP-based data communication.

An ISN is designed to randomly select a sequence number for the first byte of data transmitted in a new TCP connection.

An ISN is a random Sequence Number, allocated for the first packet in a new TCP connection.

SYN和ACK都是1bit的二进制数(即0或1)。

SYNchronize and ACKnowledge messages are indicated by a either 

When the communication between two computers ends, another 3-way communication is performed to tear down the TCP socket connection.

ISN是32bits的二进制数，是该范围内的一个随机数，用来表示这个TCP connection序列号的初始值。

还有两个很重要的值：Sequence Number, Acknowledgement Number。

在实际的数据传输过程中，一个完整的数据会被分为很多个TCP segment来传输。

每一个segment都由一个相应的序列号标记。

The FIN flag indicates the end of data transmission to finish a TCP connection.

### TCP Connection Establishment and Termination

TCP is a unicast (单播) **connection-oriented (面向连接)** protocol.

Before either end can send data to the other, a connection must be established between them.

A TCP connection is defined to be a 4-tuple consisting of two IP addresses and two port number.

It is a pair of  **endpoints** or **sockets** where each endpoint is identified by an (IP address, port number) pair. 

A connection typically goes through three phases:

1. Setup
2. Data transfer (called established)
3. Teardown (closing)

### HTTP Server

HTTP服务器本质上也是一种应用程序——它通常运行在服务器之上，绑定服务器的IP地址并监听某一个tcp端口来接收并处理HTTP请求。

HTTP conditional requests 

### Conditional headers

Several HTTP headers, called conditional headers,

## HTTP range requests

HTTP range requests allow to send only a portion of an HTTP message from a server to a client.

Partial requests are useful for large media or downloading files with pause and resume functions.

#### Range

The `Range` HTTP request header indicates the part of a document that the server should return.

Several parts can be requested with one `Range` header at once,

#### Content-Range

The `Content-Range`

#### Accept-Ranges