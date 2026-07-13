# PairingStateParam

配对状态参数。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## address

```TypeScript
address: string
```

设备地址。
长度必须为17，由16进制数字和冒号组成，形如 "11:22:33:AA:BB:FF"。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## preState

```TypeScript
preState: PairingState
```

上一个配对状态。

**类型：** PairingState

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## reason

```TypeScript
reason: PairingReason
```

配对状态原因。

**类型：** PairingReason

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## reasonMsg

```TypeScript
reasonMsg?: string
```

原因消息。此字段仅用于日志信息，不应该用于逻辑处理。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## state

```TypeScript
state: PairingState
```

当前配对状态。

**类型：** PairingState

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

