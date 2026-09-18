# BondStateParam

描述配对状态结果的参数结构。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## cause

```TypeScript
cause: UnbondCause
```

配对失败的原因。

**类型：** [UnbondCause](arkts-connectivity-connection-unbondcause-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## causeMessage

```TypeScript
causeMessage?: string
```

配对失败的具体原因，例如：本端业务主动删除配对时，返回：USER_REMOVED。

**起始版本**：26.0.0

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

配对中的对端设备地址。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## state

```TypeScript
state: BondState
```

配对状态。

**类型：** [BondState](arkts-connectivity-connection-bondstate-e.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
