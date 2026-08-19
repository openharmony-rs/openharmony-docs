# RotationLimits（系统接口）

相对于参考点的旋转角度限制

**起始版本：** 23

<!--Device-mechanicManager-export interface RotationLimits--><!--Device-mechanicManager-export interface RotationLimits-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## negativePitchMax

```TypeScript
negativePitchMax: double
```

Maximum pitch rotation angles in the negative direction, ranging from -2*Math.PI to 0, measured in radians. If the value is less than or equal to -2*Math.PI, there is no restriction.

**类型：** double

**起始版本：** 23

<!--Device-RotationLimits-negativePitchMax: double--><!--Device-RotationLimits-negativePitchMax: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## negativeRollMax

```TypeScript
negativeRollMax: double
```

Maximum roll rotation angles in the negative direction, ranging from -2*Math.PI to 0, measured in radians. If the value is less than or equal to -2*Math.PI, there is no restriction.

**类型：** double

**起始版本：** 23

<!--Device-RotationLimits-negativeRollMax: double--><!--Device-RotationLimits-negativeRollMax: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## negativeYawMax

```TypeScript
negativeYawMax: double
```

Maximum yaw rotation angles in the negative direction, ranging from -2*Math.PI to 0, measured in radians. If the value is less than or equal to -2*Math.PI, there is no restriction.

**类型：** double

**起始版本：** 23

<!--Device-RotationLimits-negativeYawMax: double--><!--Device-RotationLimits-negativeYawMax: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## positivePitchMax

```TypeScript
positivePitchMax: double
```

Maximum pitch rotation angles in the positive direction, ranging from 0 to 2*Math.PI, measured in radians. If the value is greater than or equal to 2*Math.PI, there is no restriction.

**类型：** double

**起始版本：** 23

<!--Device-RotationLimits-positivePitchMax: double--><!--Device-RotationLimits-positivePitchMax: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## positiveRollMax

```TypeScript
positiveRollMax: double
```

Maximum roll rotation angles in the positive direction, ranging from 0 to 2*Math.PI, measured in radians. If the value is greater than or equal to 2*Math.PI, there is no restriction.

**类型：** double

**起始版本：** 23

<!--Device-RotationLimits-positiveRollMax: double--><!--Device-RotationLimits-positiveRollMax: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## positiveYawMax

```TypeScript
positiveYawMax: double
```

Maximum yaw rotation angles in the positive direction, ranging from 0 to 2*Math.PI, measured in radians. If the value is greater than or equal to 2*Math.PI, there is no restriction.

**类型：** double

**起始版本：** 23

<!--Device-RotationLimits-positiveYawMax: double--><!--Device-RotationLimits-positiveYawMax: double-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

