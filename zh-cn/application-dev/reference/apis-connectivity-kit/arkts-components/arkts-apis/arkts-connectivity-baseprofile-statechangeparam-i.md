# StateChangeParam

本端和对端蓝牙设备间Profile连接状态变化参数。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { baseProfile } from '@kit.ConnectivityKit';
```

## cause

```TypeScript
cause: DisconnectCause
```

Profile断开连接的原因。

**类型：** [DisconnectCause](arkts-connectivity-baseprofile-disconnectcause-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

对端设备地址，例如："XX:XX:XX:XX:XX:XX"。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## role

```TypeScript
role?: PanRole
```

当前对端设备对应的PAN角色。仅PAN Profile连接状态发生变化时返回该字段，非PAN场景下该字段不存在。

**类型：** [PanRole](arkts-connectivity-baseprofile-panrole-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## state

```TypeScript
state: ProfileConnectionState
```

Profile连接状态。

**类型：** [ProfileConnectionState](arkts-connectivity-baseprofile-profileconnectionstate-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
