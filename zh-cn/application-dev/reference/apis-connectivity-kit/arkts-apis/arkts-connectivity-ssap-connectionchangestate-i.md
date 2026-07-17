# ConnectionChangeState

描述SSAP连接状态。

**起始版本：** 26.0.0

<!--Device-ssap-interface ConnectionChangeState--><!--Device-ssap-interface ConnectionChangeState-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

设备地址。长度必须为17，由16进制数字和冒号组成，形如 "11:22:33:AA:BB:FF"。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectionChangeState-address: string--><!--Device-ConnectionChangeState-address: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## state

```TypeScript
state: ConnectionState
```

连接状态。

**类型：** ConnectionState

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectionChangeState-state: ConnectionState--><!--Device-ConnectionChangeState-state: ConnectionState-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

