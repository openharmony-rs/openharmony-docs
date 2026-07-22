# RotationAxesStatus（系统接口）

Rotation axes status

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

是否使能俯仰轴

**类型：** boolean

**起始版本：** 20

<!--Device-RotationAxesStatus-pitchEnabled: boolean--><!--Device-RotationAxesStatus-pitchEnabled: boolean-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## pitchLimited

```TypeScript
pitchLimited?: RotationAxisLimited
```

Whether the pitch axis is limited.

**类型：** RotationAxisLimited

**起始版本：** 20

<!--Device-RotationAxesStatus-pitchLimited?: RotationAxisLimited--><!--Device-RotationAxesStatus-pitchLimited?: RotationAxisLimited-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## rollEnabled

```TypeScript
rollEnabled: boolean
```

是否启用滚动轴

**类型：** boolean

**起始版本：** 20

<!--Device-RotationAxesStatus-rollEnabled: boolean--><!--Device-RotationAxesStatus-rollEnabled: boolean-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## rollLimited

```TypeScript
rollLimited?: RotationAxisLimited
```

Whether the roll axis is limited.

**类型：** RotationAxisLimited

**起始版本：** 20

<!--Device-RotationAxesStatus-rollLimited?: RotationAxisLimited--><!--Device-RotationAxesStatus-rollLimited?: RotationAxisLimited-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## yawEnabled

```TypeScript
yawEnabled: boolean
```

是否启用偏航轴

**类型：** boolean

**起始版本：** 20

<!--Device-RotationAxesStatus-yawEnabled: boolean--><!--Device-RotationAxesStatus-yawEnabled: boolean-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## yawLimited

```TypeScript
yawLimited?: RotationAxisLimited
```

偏航轴是否限位

**类型：** RotationAxisLimited

**起始版本：** 20

<!--Device-RotationAxesStatus-yawLimited?: RotationAxisLimited--><!--Device-RotationAxesStatus-yawLimited?: RotationAxisLimited-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

