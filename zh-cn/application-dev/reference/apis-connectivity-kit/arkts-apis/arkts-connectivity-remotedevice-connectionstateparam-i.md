# ConnectionStateParam

连接状态参数。

**起始版本：** 26.0.0

<!--Device-remoteDevice-interface ConnectionStateParam--><!--Device-remoteDevice-interface ConnectionStateParam-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

设备地址。长度必须为17，由16进制数字和冒号组成，形如 "11:22:33:AA:BB:FF"。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectionStateParam-address: string--><!--Device-ConnectionStateParam-address: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## connectionReason

```TypeScript
connectionReason: ConnectionReason
```

连接原因。

**类型：** ConnectionReason

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectionStateParam-connectionReason: ConnectionReason--><!--Device-ConnectionStateParam-connectionReason: ConnectionReason-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## preState

```TypeScript
preState: ConnectionState
```

上一个连接状态。

**类型：** ConnectionState

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectionStateParam-preState: ConnectionState--><!--Device-ConnectionStateParam-preState: ConnectionState-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## reasonMsg

```TypeScript
reasonMsg?: string
```

原因消息。此字段仅用于日志信息，不应该用于逻辑处理。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectionStateParam-reasonMsg?: string--><!--Device-ConnectionStateParam-reasonMsg?: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## state

```TypeScript
state: ConnectionState
```

当前连接状态。

**类型：** ConnectionState

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectionStateParam-state: ConnectionState--><!--Device-ConnectionStateParam-state: ConnectionState-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

