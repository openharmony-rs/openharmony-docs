# TCPConnectOptions

TCPSocket连接的参数。

**起始版本：** 7

<!--Device-socket-export interface TCPConnectOptions--><!--Device-socket-export interface TCPConnectOptions-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## address

```TypeScript
address: NetAddress
```

绑定的地址以及端口。

**类型：** NetAddress

**起始版本：** 7

<!--Device-TCPConnectOptions-address: NetAddress--><!--Device-TCPConnectOptions-address: NetAddress-End-->

**系统能力：** SystemCapability.Communication.NetStack

## proxy

```TypeScript
proxy?: ProxyOptions
```

使用的代理信息，默认不使用代理。

**类型：** [ProxyOptions](arkts-network-socket-proxyoptions-i.md)

**起始版本：** 18

<!--Device-TCPConnectOptions-proxy?: ProxyOptions--><!--Device-TCPConnectOptions-proxy?: ProxyOptions-End-->

**系统能力：** SystemCapability.Communication.NetStack

## timeout

```TypeScript
timeout?: int
```

超时时间，单位毫秒（ms）。默认值为5000。

**类型：** int

**起始版本：** 7

<!--Device-TCPConnectOptions-timeout?: int--><!--Device-TCPConnectOptions-timeout?: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

