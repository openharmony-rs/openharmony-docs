# ProxyOptions

Socket代理信息。

**起始版本：** 18

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## address

```TypeScript
address: NetAddress
```

代理地址信息。

**类型：** NetAddress

**起始版本：** 18

**系统能力：** SystemCapability.Communication.NetStack

## password

```TypeScript
password?: string
```

指定密码，如果使用用户密码验证方式。

**类型：** string

**起始版本：** 18

**系统能力：** SystemCapability.Communication.NetStack

## type

```TypeScript
type: ProxyTypes
```

代理类型。

**类型：** [ProxyTypes](arkts-network-socket-proxytypes-e.md)

**起始版本：** 18

**系统能力：** SystemCapability.Communication.NetStack

## username

```TypeScript
username?: string
```

指定用户名，如果使用用户密码验证方式。

**类型：** string

**起始版本：** 18

**系统能力：** SystemCapability.Communication.NetStack
