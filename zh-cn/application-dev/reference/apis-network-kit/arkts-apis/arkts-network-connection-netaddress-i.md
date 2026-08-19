# NetAddress

网络地址。

**起始版本：** 23

<!--Device-connection-export interface NetAddress--><!--Device-connection-export interface NetAddress-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## address

```TypeScript
address: string
```

地址。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NetAddress-address: string--><!--Device-NetAddress-address: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## family

```TypeScript
family?: int
```

IPv4 = 1，IPv6 = 2，默认IPv4。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NetAddress-family?: int--><!--Device-NetAddress-family?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## port

```TypeScript
port?: int
```

端口，取值范围[0, 65535]，默认值为0。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NetAddress-port?: int--><!--Device-NetAddress-port?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

