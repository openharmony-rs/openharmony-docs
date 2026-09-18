# AclStateResult

描述ACL连接状态的参数结构。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId: string
```

表示对端设备的地址，例如："XX:XX:XX:XX:XX:XX"。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## state

```TypeScript
state: AclState
```

连接状态。

**类型：** [AclState](arkts-connectivity-connection-aclstate-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
