# SpeedParams（系统接口）

Parameters for moving or turning at a speed.

**起始版本：** 26.0.0

<!--Device-mechanicManager-export interface SpeedParams--><!--Device-mechanicManager-export interface SpeedParams-End-->

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

<!--Device-SpeedParams-angle: double--><!--Device-SpeedParams-angle: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## mode

```TypeScript
mode?: MarchingMode
```

Movement mode.

**类型：** MarchingMode

**起始版本：** 26.0.0

<!--Device-SpeedParams-mode?: MarchingMode--><!--Device-SpeedParams-mode?: MarchingMode-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## speed

```TypeScript
speed: number
```

Turning or moving speed, unit cm.The value should be an integer.

**类型：** number

**起始版本：** 26.0.0

<!--Device-SpeedParams-speed: int--><!--Device-SpeedParams-speed: int-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

