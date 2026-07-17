# MoveParams（系统接口）

Parameters for moving the target.

**起始版本：** 26.0.0

<!--Device-mechanicManager-export interface MoveParams--><!--Device-mechanicManager-export interface MoveParams-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## angle

```TypeScript
angle: number
```

Turning angle, unit degree.

**类型：** number

**起始版本：** 26.0.0

<!--Device-MoveParams-angle: double--><!--Device-MoveParams-angle: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## distance

```TypeScript
distance: number
```

Moving distance, unit cm.The value should be an integer.

**类型：** number

**起始版本：** 26.0.0

<!--Device-MoveParams-distance: int--><!--Device-MoveParams-distance: int-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## mode

```TypeScript
mode?: MarchingMode
```

Movement mode.

**类型：** MarchingMode

**起始版本：** 26.0.0

<!--Device-MoveParams-mode?: MarchingMode--><!--Device-MoveParams-mode?: MarchingMode-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## speedGear

```TypeScript
speedGear?: SpeedGear
```

Speed gear.

**类型：** SpeedGear

**起始版本：** 26.0.0

<!--Device-MoveParams-speedGear?: SpeedGear--><!--Device-MoveParams-speedGear?: SpeedGear-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

