# LocalConnectOptions

LocalSocket客户端在连接服务端时传入的参数信息。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## address

```TypeScript
address: LocalAddress
```

本地套接字路径。

**类型：** [LocalAddress](arkts-network-socket-localaddress-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack

## timeout

```TypeScript
timeout?: number
```

连接服务端的超时时间，单位为毫秒。默认值为0。需要应用手动设置一下，建议设置为5000。

**类型：** number

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack
