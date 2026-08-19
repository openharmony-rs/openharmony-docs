# UDPSendOptions

UDPSocket发送参数。

**起始版本：** 7

<!--Device-socket-export interface UDPSendOptions--><!--Device-socket-export interface UDPSendOptions-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## address

```TypeScript
address: NetAddress
```

目标地址信息。

**类型：** NetAddress

**起始版本：** 7

<!--Device-UDPSendOptions-address: NetAddress--><!--Device-UDPSendOptions-address: NetAddress-End-->

**系统能力：** SystemCapability.Communication.NetStack

## data

```TypeScript
data: string | ArrayBuffer
```

发送的数据。

**类型：** string \| ArrayBuffer

**起始版本：** 7

<!--Device-UDPSendOptions-data: string | ArrayBuffer--><!--Device-UDPSendOptions-data: string | ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.NetStack

## proxy

```TypeScript
proxy?: ProxyOptions
```

使用的代理信息，默认不使用代理。

**类型：** [ProxyOptions](arkts-network-socket-proxyoptions-i.md)

**起始版本：** 18

<!--Device-UDPSendOptions-proxy?: ProxyOptions--><!--Device-UDPSendOptions-proxy?: ProxyOptions-End-->

**系统能力：** SystemCapability.Communication.NetStack

