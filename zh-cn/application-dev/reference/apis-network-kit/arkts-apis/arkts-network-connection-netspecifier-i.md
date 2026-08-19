# NetSpecifier

提供承载数据网络能力的实例。

**起始版本：** 23

<!--Device-connection-export interface NetSpecifier--><!--Device-connection-export interface NetSpecifier-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## bearerPrivateIdentifier

```TypeScript
bearerPrivateIdentifier?: string
```

网络标识符，蜂窝网络的标识符是"slot0"（对应SIM卡1）、"slot1"（对应SIM卡2）。从API12开始可以通过传递注册的WLAN热点信息表示应用希望激活的指定的WLAN网络。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NetSpecifier-bearerPrivateIdentifier?: string--><!--Device-NetSpecifier-bearerPrivateIdentifier?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## netCapabilities

```TypeScript
netCapabilities: NetCapabilities
```

存储数据网络的传输能力和承载类型。

**类型：** [NetCapabilities](arkts-network-connection-netcapabilities-i.md)

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NetSpecifier-netCapabilities: NetCapabilities--><!--Device-NetSpecifier-netCapabilities: NetCapabilities-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

