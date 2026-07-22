# RotationAngles（系统接口）

The rotion angles, relative to the current position.

**起始版本：** 20

<!--Device-mechanicManager-export interface RotationAngles--><!--Device-mechanicManager-export interface RotationAngles-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## pitch

```TypeScript
pitch?: number
```

俯仰角，范围从-2π到2*π，以弧度为单位。

**类型：** number

**起始版本：** 20

<!--Device-RotationAngles-pitch?: double--><!--Device-RotationAngles-pitch?: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## roll

```TypeScript
roll?: number
```

滚动角度，范围从-2π到2*π，以弧度为单位。

**类型：** number

**起始版本：** 20

<!--Device-RotationAngles-roll?: double--><!--Device-RotationAngles-roll?: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## yaw

```TypeScript
yaw?: number
```

偏航角，范围从-2π到2*π，以弧度为单位。

**类型：** number

**起始版本：** 20

<!--Device-RotationAngles-yaw?: double--><!--Device-RotationAngles-yaw?: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

