# BatteryLevelInfo（系统接口）

```TypeScript
export interface BatteryLevelInfo
```

设备电池电量信息

**起始版本：** 26.2.0

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## batteryLevel

```TypeScript
batteryLevel: number
```

电池电量值的百分比。取值限定为整数。

**类型：** number

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## isCharging

```TypeScript
isCharging: boolean
```

是否在充电。

**类型：** boolean

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## mechId

```TypeScript
mechId: number
```

ID of the mechanical device. ID of the mechanical device. ID of the mechanical device.设备ID。取值限定为整数。

**类型：** number

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。
