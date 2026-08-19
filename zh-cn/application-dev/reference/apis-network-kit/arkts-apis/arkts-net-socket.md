# @ohos.net.socket

本模块提供利用Socket进行数据传输的能力，支持TCPSocket、UDPSocket、WebSocket和TLSSocket。 > **说明：** > > 本模块API使用时建议放在worker线程或者taskpool中做网络操作，否则可能会导致UI线程卡顿。

**起始版本：** 7

<!--Device-unnamed-declare namespace socket--><!--Device-unnamed-declare namespace socket-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [constructLocalSocketInstance](arkts-network-socket-constructlocalsocketinstance-f.md) | 创建一个LocalSocket对象。 |
| [constructLocalSocketServerInstance](arkts-network-socket-constructlocalsocketserverinstance-f.md) | 创建一个LocalSocketServer对象。 |
| [constructMulticastSocketInstance](arkts-network-socket-constructmulticastsocketinstance-f.md) | 创建一个MulticastSocket对象。 |
| [constructTCPSocketInstance](arkts-network-socket-constructtcpsocketinstance-f.md) | 创建一个TCPSocket对象。 |
| [constructTCPSocketServerInstance](arkts-network-socket-constructtcpsocketserverinstance-f.md) | 创建一个TCPSocketServer对象。 |
| [constructTLSSocketInstance](arkts-network-socket-constructtlssocketinstance-f.md) | 创建并返回一个TLSSocket对象。 |
| [constructTLSSocketInstance](arkts-network-socket-constructtlssocketinstance-f.md) | 将TCPSocket升级为TLSSocket，创建并返回一个TLSSocket对象。 |
| [constructTLSSocketServerInstance](arkts-network-socket-constructtlssocketserverinstance-f.md) | 创建并返回一个TLSSocketServer对象。 |
| [constructUDPSocketInstance](arkts-network-socket-constructudpsocketinstance-f.md) | 创建一个UDPSocket对象。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md) | Socket套接字的基础属性。 |
| [LocalAddress](arkts-network-socket-localaddress-i.md) | LocalSocket本地套接字文件路径信息，在传入套接字路径进行绑定时，会在此路径下创建套接字文件。 |
| [LocalConnectOptions](arkts-network-socket-localconnectoptions-i.md) | LocalSocket客户端在连接服务端时传入的参数信息。 |
| [LocalSendOptions](arkts-network-socket-localsendoptions-i.md) | LocalSocket发送请求的参数。 |
| [LocalSocket](arkts-network-socket-localsocket-i.md) | LocalSocket连接。在调用LocalSocket的方法前，需要先通过 [socket.constructLocalSocketInstance](arkts-network-socket-constructlocalsocketinstance-f.md)创建LocalSocket对象。 |
| [LocalSocketConnection](arkts-network-socket-localsocketconnection-i.md) | LocalSocketConnection连接，即LocalSocket客户端与服务端的会话连接。在调用LocalSocketConnection的方法前，需要先获取LocalSocketConnection对象。 |
| [LocalSocketMessageInfo](arkts-network-socket-localsocketmessageinfo-i.md) | LocalSocket客户端与服务端通信时接收的数据。 |
| [LocalSocketServer](arkts-network-socket-localsocketserver-i.md) | LocalSocketServer类。在调用LocalSocketServer的方法前，需要先通过 [socket.constructLocalSocketServerInstance](arkts-network-socket-constructlocalsocketserverinstance-f.md)创建LocalSocketServer对象。 |
| [MulticastSocket](arkts-network-socket-multicastsocket-i.md) | MulticastSocket连接。在调用MulticastSocket的方法前，需要先通过 [socket.constructMulticastSocketInstance](arkts-network-socket-constructmulticastsocketinstance-f.md)创建MulticastSocket对象。 |
| [ProxyOptions](arkts-network-socket-proxyoptions-i.md) | Socket代理信息。 |
| [SocketMessageInfo](arkts-network-socket-socketmessageinfo-i.md) | socket连接信息 |
| [SocketRemoteInfo](arkts-network-socket-socketremoteinfo-i.md) | Socket的连接信息。 |
| [SocketStateBase](arkts-network-socket-socketstatebase-i.md) | Socket的状态信息。 |
| [TCPConnectOptions](arkts-network-socket-tcpconnectoptions-i.md) | TCPSocket连接的参数。 |
| [TCPExtraOptions](arkts-network-socket-tcpextraoptions-i.md) | TCPSocket连接的其他属性。继承自[ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md)。 |
| [TCPSendOptions](arkts-network-socket-tcpsendoptions-i.md) | TCPSocket发送请求的参数。 |
| [TCPSocket](arkts-network-socket-tcpsocket-i.md) | TCPSocket连接。在调用TCPSocket的方法前，需要先通过[socket.constructTCPSocketInstance](arkts-network-socket-constructtcpsocketinstance-f.md)创建 TCPSocket对象。 |
| [TCPSocketConnection](arkts-network-socket-tcpsocketconnection-i.md) | TCPSocketConnection连接，即TCPSocket客户端与服务端的连接。在调用TCPSocketConnection的方法前，需要先获取TCPSocketConnection对象。 |
| [TCPSocketServer](arkts-network-socket-tcpsocketserver-i.md) | TCPSocketServer连接。在调用TCPSocketServer的方法前，需要先通过 [socket.constructTCPSocketServerInstance](arkts-network-socket-constructtcpsocketserverinstance-f.md)创建TCPSocketServer对象。 |
| [TLSConnectOptions](arkts-network-socket-tlsconnectoptions-i.md) | TLS连接的操作。 |
| [TLSSecureOptions](arkts-network-socket-tlssecureoptions-i.md) | TLS安全相关操作。当本地证书cert和私钥key不为空时，开启双向验证模式。cert和key其中一项为空时，开启单向验证模式。 |
| [TLSSocket](arkts-network-socket-tlssocket-i.md) | TLSSocket连接。在调用TLSSocket的方法前，需要先通过[socket.constructTLSSocketInstance](arkts-network-socket-constructtlssocketinstance-f.md)创建 TLSSocket对象。 |
| [TLSSocketConnection](arkts-network-socket-tlssocketconnection-i.md) | TLSSocketConnection连接，即TLSSocket客户端与服务端的连接。在调用TLSSocketConnection的方法前，需要先获取TLSSocketConnection对象。 |
| [TLSSocketServer](arkts-network-socket-tlssocketserver-i.md) | TLSSocketServer连接。在调用TLSSocketServer的方法前，需要先通过 [socket.constructTLSSocketServerInstance](arkts-network-socket-constructtlssocketserverinstance-f.md)创建TLSSocketServer对象。 |
| [UDPExtraOptions](arkts-network-socket-udpextraoptions-i.md) | UDPSocket连接的其他属性。继承自[ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md)。 |
| [UDPSendOptions](arkts-network-socket-udpsendoptions-i.md) | UDPSocket发送参数。 |
| [UDPSocket](arkts-network-socket-udpsocket-i.md) | UDPSocket连接。在调用UDPSocket的方法前，需要先通过[socket.constructUDPSocketInstance](arkts-network-socket-constructudpsocketinstance-f.md)创建 UDPSocket对象。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Protocol](arkts-network-socket-protocol-e.md) | TLS通信的协议版本。 |
| [ProxyTypes](arkts-network-socket-proxytypes-e.md) | Socket代理类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [X509CertRawData](arkts-network-socket-x509certrawdata-t.md) | 存储证书的数据。 |

