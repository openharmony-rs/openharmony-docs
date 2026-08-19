# SocketRemoteInfo

Socket的连接信息。

**起始版本：** 7

<!--Device-socket-export interface SocketRemoteInfo--><!--Device-socket-export interface SocketRemoteInfo-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## address

```TypeScript
address: string
```

对端的IP地址。

**类型：** string

**起始版本：** 7

<!--Device-SocketRemoteInfo-address: string--><!--Device-SocketRemoteInfo-address: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## family

```TypeScript
family: 'IPv4' | 'IPv6'
```

网络协议类型，可选类型： - IPv4 - IPv6 默认为IPv4。

**类型：** 'IPv4' \| 'IPv6'

**起始版本：** 7

<!--Device-SocketRemoteInfo-family: 'IPv4' | 'IPv6'--><!--Device-SocketRemoteInfo-family: 'IPv4' | 'IPv6'-End-->

**系统能力：** SystemCapability.Communication.NetStack

## port

```TypeScript
port: int
```

端口号，范围0~65535。

**类型：** int

**起始版本：** 7

<!--Device-SocketRemoteInfo-port: int--><!--Device-SocketRemoteInfo-port: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

## size

```TypeScript
size: int
```

服务器响应信息的字节长度。

**类型：** int

**起始版本：** 7

<!--Device-SocketRemoteInfo-size: int--><!--Device-SocketRemoteInfo-size: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

