# SocketRemoteInfo

Socket的连接信息。

**起始版本：** 7

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

**系统能力：** SystemCapability.Communication.NetStack

## family

```TypeScript
family: 'IPv4' | 'IPv6'
```

网络协议类型，可选类型：  
- IPv4  
- IPv6  
默认为IPv4。

**类型：** 'IPv4' \| 'IPv6'

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NetStack

## port

```TypeScript
port: number
```

端口号，范围0~65535。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NetStack

## size

```TypeScript
size: number
```

服务器响应信息的字节长度。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NetStack
