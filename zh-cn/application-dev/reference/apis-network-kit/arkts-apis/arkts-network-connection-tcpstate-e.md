# TcpState

TCP状态。

**起始版本：** 24

<!--Device-connection-export enum TcpState--><!--Device-connection-export enum TcpState-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## TCP_ESTABLISHED

```TypeScript
TCP_ESTABLISHED = 1
```

连接已建立，可正常收发数据。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpState-TCP_ESTABLISHED = 1--><!--Device-TcpState-TCP_ESTABLISHED = 1-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## TCP_SYN_SENT

```TypeScript
TCP_SYN_SENT = 2
```

客户端发送SYN，等待服务端ACK+SYN（三次握手的第一步）。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpState-TCP_SYN_SENT = 2--><!--Device-TcpState-TCP_SYN_SENT = 2-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## TCP_SYN_RECV

```TypeScript
TCP_SYN_RECV = 3
```

服务端接收SYN并发送ACK+SYN，等待客户端ACK（三次握手的第二步）。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpState-TCP_SYN_RECV = 3--><!--Device-TcpState-TCP_SYN_RECV = 3-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## TCP_FIN_WAIT1

```TypeScript
TCP_FIN_WAIT1 = 4
```

主动端发送FIN，等待对方ACK。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpState-TCP_FIN_WAIT1 = 4--><!--Device-TcpState-TCP_FIN_WAIT1 = 4-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## TCP_FIN_WAIT2

```TypeScript
TCP_FIN_WAIT2 = 5
```

主动端接收FIN的ACK，等待对方ACK。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpState-TCP_FIN_WAIT2 = 5--><!--Device-TcpState-TCP_FIN_WAIT2 = 5-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## TCP_TIME_WAIT

```TypeScript
TCP_TIME_WAIT = 6
```

主动端接收对方FIN并回复ACK，等待2倍最大报文段生存时间后彻底释放。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpState-TCP_TIME_WAIT = 6--><!--Device-TcpState-TCP_TIME_WAIT = 6-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## TCP_CLOSE

```TypeScript
TCP_CLOSE = 7
```

初始/关闭状态，无连接。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpState-TCP_CLOSE = 7--><!--Device-TcpState-TCP_CLOSE = 7-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## TCP_CLOSE_WAIT

```TypeScript
TCP_CLOSE_WAIT = 8
```

被动端接收FIN并发送ACK，等待对方FIN。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpState-TCP_CLOSE_WAIT = 8--><!--Device-TcpState-TCP_CLOSE_WAIT = 8-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## TCP_LAST_ACK

```TypeScript
TCP_LAST_ACK = 9
```

被动端发送FIN后，等待对方ACK。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpState-TCP_LAST_ACK = 9--><!--Device-TcpState-TCP_LAST_ACK = 9-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## TCP_LISTEN

```TypeScript
TCP_LISTEN = 10
```

服务端监听，等待客户端连接。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpState-TCP_LISTEN = 10--><!--Device-TcpState-TCP_LISTEN = 10-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## TCP_CLOSING

```TypeScript
TCP_CLOSING = 11
```

双方同时发送FIN，互相等待ACK。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpState-TCP_CLOSING = 11--><!--Device-TcpState-TCP_CLOSING = 11-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

