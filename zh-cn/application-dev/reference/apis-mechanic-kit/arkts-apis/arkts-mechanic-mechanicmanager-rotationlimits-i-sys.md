# RotationLimits（系统接口）

```TypeScript
export interface RotationLimits
```

相对于参考点的旋转角度限制@typedef RotationLimits

**起始版本：** 20

<!--Device-mechanicManager-export interface RotationLimits--><!--Device-mechanicManager-export interface RotationLimits-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## negativePitchMax

```TypeScript
negativePitchMax: number
```

最大俯仰旋转角度（负方向），范围为[-2*Math.PI， 0]，以弧度为单位。如果值小于或等于 -2*Math.PI，则没有限制。

**类型：** number

**起始版本：** 20

<!--Device-RotationLimits-negativePitchMax: double--><!--Device-RotationLimits-negativePitchMax: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## negativeRollMax

```TypeScript
negativeRollMax: number
```

最大横滚旋转角度（负方向），范围为[-2*Math.PI, 0]，以弧度为单位。如果值小于或等于 -2*Math.PI，则没有限制。

**类型：** number

**起始版本：** 20

<!--Device-RotationLimits-negativeRollMax: double--><!--Device-RotationLimits-negativeRollMax: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## negativeYawMax

```TypeScript
negativeYawMax: number
```

最大偏航旋转角度（负方向），范围为[-2*Math.PI， 0]，以弧度为单位如果值小于或等于 -2*Math.PI，则没有限制。

**类型：** number

**起始版本：** 20

<!--Device-RotationLimits-negativeYawMax: double--><!--Device-RotationLimits-negativeYawMax: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## positivePitchMax

```TypeScript
positivePitchMax: number
```

最大俯仰旋转角度（正方向），范围为[0， 2*Math.PI]，以弧度为单位。如果值大于或等于 2*Math.PI，则没有限制。

**类型：** number

**起始版本：** 20

<!--Device-RotationLimits-positivePitchMax: double--><!--Device-RotationLimits-positivePitchMax: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## positiveRollMax

```TypeScript
positiveRollMax: number
```

最大横滚旋转角度（正方向），范围为[0， 2*Math.PI]，以弧度为单位。如果值大于或等于 2*Math.PI，则没有限制。

**类型：** number

**起始版本：** 20

<!--Device-RotationLimits-positiveRollMax: double--><!--Device-RotationLimits-positiveRollMax: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## positiveYawMax

```TypeScript
positiveYawMax: number
```

最大偏航旋转角度（正方向），范围为[0， 2*Math.PI]，以弧度为单位。如果值大于或等于 2*Math.PI，则没有限制。

**类型：** number

**起始版本：** 20

<!--Device-RotationLimits-positiveYawMax: double--><!--Device-RotationLimits-positiveYawMax: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。
