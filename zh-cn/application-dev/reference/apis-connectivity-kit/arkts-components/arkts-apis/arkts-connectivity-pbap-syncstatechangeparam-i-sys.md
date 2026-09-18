# SyncStateChangeParam（系统接口）

电话本同步状态变化信息。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { pbap } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId: string
```

远程设备的地址。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state: SyncStateType
```

电话簿同步状态。

**类型：** [SyncStateType](arkts-connectivity-pbap-syncstatetype-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。
