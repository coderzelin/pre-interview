### TCP

#### TCP特性

- TCP提供一种面向连接、可靠的字节流服务
- 在一个TCP链接中，仅有两方进行彼此通讯，广播和多播不能用于TCP
- TCP使用校验，确认和重传机制来保证可靠传输
- TCP给数据分节进行排序，并使用累积确认保证数据份顺序不变和非重复
- TCP使用滑动窗口来实现流量控制，通过动态改变窗口大小进行拥塞机制

#### TCP和UDP的区别

- TCP是面向连接的可靠的传输协议，UDP是面向无连接的不可靠的传输协议
- TCP会对数据进行分节排序，会保证数据传输的有序性，UDP不会对数据进行分节，不保证数据传输的有序性
- TCP有拥塞机制，TCP无丢包情况，UDP没有拥塞机制，容易丢包
- TCP传输速度慢，传输数据大，UDP传输速度快，传输数据小
- TCP只能单播，UDP可以广播和多播

#### TCP 三次握手
目的：TCP是可靠的传输协议，他的本质是要确定客户端和服务端，他们的发送和接收能力是没问题的，也就是客户端要确定服务端的发送和接收能力没问题，同时，服务端也要确定客户端的发送和接收能力没问题

- 第一次握手(SYN=1)
  - 客户端发送一个SYN标志位置为1的包给服务端，指明客户端想要连接服务端的端口，发送完毕后，客户端进入`SYN_SEND`状态
- 第二次握手(SYN=1,ACK=1)
  - 服务端发送SYN标志位1和确认包ACK为1应答客户端，发送完毕后，服务端进入`SYN_RCVD`状态
- 第三次握手(ACK=1)
  - 客户端再次发送确认包ACK给服务端，发送完毕后，客户端进入`ESTABLISHED`状态，当服务端接收到客户端的ACK包，也进入`ESTABLISHED`状态，TCP握手结束

#### TCP四次挥手
断开TCP连接需要发送四个包，这个过程叫做四次挥手，客户端和服务端都可以主动断开连接

- 第一次挥手(FIN=1)
  - 假设客户端想要断开连接，客户端发送一个FIN标志位置为1的包给服务端，表明自己没有数据可以传了，但是还是可以接收数据，发送完毕后，客户端进入`FIN_WAIT_1`状态
- 第二次挥手(ACK=1)
  - 服务端发送ACK确认包给客户端，表示服务端已接收到客户端断开连接的请求，但是自己还没准备好关闭连接，发送完毕后，服务端进入`CLOSE_WAIT`状态，客户端接收到确认包后，进入`FIN_WAIT_2`状态，等待服务端关闭连接
- 第三次挥手(FIN=1)
  - 服务端准备关闭连接时，向客户端发送关闭连接请求，发送FIN标志位置1的包给客户端，发送完毕后，服务端进入`LAST_ACK`状态，等待客户端发送最后一个ACK包
- 第四次挥手(ACK=1)
  - 客户端收到服务端的关闭请求后，发送ACK确认包给服务端，客户端进入`TIME_WAIT`状态，等待服务端重传的ACK包，服务端接收的客户端的ACK包后，关闭连接，进入`CLOSED`状态，客户端等待了2MSL时间后，没有收到服务端的ACK，认为服务端已经关闭连接，于是自己也关闭连接，进入`CLOSED`状态