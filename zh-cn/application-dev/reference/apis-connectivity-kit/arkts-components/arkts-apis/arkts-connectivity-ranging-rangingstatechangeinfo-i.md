# RangingStateChangeInfo

描述测距状态变化信息，主动测距和被动测距的状态变化共用此结构。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## 导入模块

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## cause

```TypeScript
cause: RangingStoppedCause
```

测距停止原因，仅在state为RANGING_STOPPED时有意义。

**类型：** [RangingStoppedCause](arkts-connectivity-ranging-rangingstoppedcause-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## deviceId

```TypeScript
deviceId?: string
```

测距设备的地址, 主动测距场景下标识发生状态变化的目标设备。被动测距场景下该字段不适用，默认值为undefined

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## handle

```TypeScript
handle?: number
```

测距监控句柄，被动测距场景下标识发生状态变化的被动测距会话。主动测距场景下该字段不适用，默认值为undefined。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## state

```TypeScript
state: RangingState
```

测距状态。

**类型：** [RangingState](arkts-connectivity-ranging-rangingstate-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core
