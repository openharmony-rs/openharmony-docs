# ConnectionResult

连接结果的参数说明。

**起始版本：** 26.0.0

<!--Device-dataTransfer-interface ConnectionResult--><!--Device-dataTransfer-interface ConnectionResult-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { dataTransfer } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

连接的设备地址。长度必须为17，由十六进制数字和冒号组成，例如：11:22:33:AA:BB:FF。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectionResult-address: string--><!--Device-ConnectionResult-address: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## mtu

```TypeScript
mtu: number
```

通道数据的最大长度单位为： 字节，取值应为[0,65535]内的整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectionResult-mtu: int--><!--Device-ConnectionResult-mtu: int-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## state

```TypeScript
state: ConnectionState
```

连接状态。

**类型：** ConnectionState

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectionResult-state: ConnectionState--><!--Device-ConnectionResult-state: ConnectionState-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## uuid

```TypeScript
uuid: string
```

服务ID。长度必须为36，由16进制数字字符和连字符共36个字符组成，形如“FFFFFFFF-1234-5678-ABCD-000000001234”，代表128比特标识。<br>禁止使用星闪标准服务UUID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectionResult-uuid: string--><!--Device-ConnectionResult-uuid: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

