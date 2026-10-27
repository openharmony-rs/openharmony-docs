# RotationAxesStatus（系统接口）

```TypeScript
export interface RotationAxesStatus
```

旋转轴状态

**起始版本：** 20

<!--Device-mechanicManager-export interface RotationAxesStatus--><!--Device-mechanicManager-export interface RotationAxesStatus-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## pitchEnabled

```TypeScript
pitchEnabled: boolean
```

是否启用了俯仰轴，true表示已启用，false表示已禁用。

**类型：** boolean

**起始版本：** 20

<!--Device-RotationAxesStatus-pitchEnabled: boolean--><!--Device-RotationAxesStatus-pitchEnabled: boolean-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## pitchLimited

```TypeScript
pitchLimited?: RotationAxisLimited
```

俯仰轴限位状态

**类型：** [RotationAxisLimited](arkts-mechanic-mechanicmanager-rotationaxislimited-e-sys.md)

**起始版本：** 20

<!--Device-RotationAxesStatus-pitchLimited?: RotationAxisLimited--><!--Device-RotationAxesStatus-pitchLimited?: RotationAxisLimited-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## rollEnabled

```TypeScript
rollEnabled: boolean
```

是否启用了横滚轴，true表示已启用，false表示已禁用。

**类型：** boolean

**起始版本：** 20

<!--Device-RotationAxesStatus-rollEnabled: boolean--><!--Device-RotationAxesStatus-rollEnabled: boolean-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## rollLimited

```TypeScript
rollLimited?: RotationAxisLimited
```

横滚轴限位状态

**类型：** [RotationAxisLimited](arkts-mechanic-mechanicmanager-rotationaxislimited-e-sys.md)

**起始版本：** 20

<!--Device-RotationAxesStatus-rollLimited?: RotationAxisLimited--><!--Device-RotationAxesStatus-rollLimited?: RotationAxisLimited-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## yawEnabled

```TypeScript
yawEnabled: boolean
```

是否启用了偏航轴，true表示已启用，false表示已禁用。

**类型：** boolean

**起始版本：** 20

<!--Device-RotationAxesStatus-yawEnabled: boolean--><!--Device-RotationAxesStatus-yawEnabled: boolean-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## yawLimited

```TypeScript
yawLimited?: RotationAxisLimited
```

偏航轴限位状态

**类型：** [RotationAxisLimited](arkts-mechanic-mechanicmanager-rotationaxislimited-e-sys.md)

**起始版本：** 20

<!--Device-RotationAxesStatus-yawLimited?: RotationAxisLimited--><!--Device-RotationAxesStatus-yawLimited?: RotationAxisLimited-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。
