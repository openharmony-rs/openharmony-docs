# MoveParams（系统接口）

设备移动参数

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

转动角度。

**类型：** number

**起始版本：** 26.0.0

<!--Device-MoveParams-angle: double--><!--Device-MoveParams-angle: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## distance

```TypeScript
distance: number
```

移动距离。取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

<!--Device-MoveParams-distance: int--><!--Device-MoveParams-distance: int-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## mode

```TypeScript
mode?: MarchingMode
```

行进方式。

**类型：** MarchingMode

**起始版本：** 26.0.0

<!--Device-MoveParams-mode?: MarchingMode--><!--Device-MoveParams-mode?: MarchingMode-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## speedGear

```TypeScript
speedGear?: SpeedGear
```

速度档位。

**类型：** SpeedGear

**起始版本：** 26.0.0

<!--Device-MoveParams-speedGear?: SpeedGear--><!--Device-MoveParams-speedGear?: SpeedGear-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

