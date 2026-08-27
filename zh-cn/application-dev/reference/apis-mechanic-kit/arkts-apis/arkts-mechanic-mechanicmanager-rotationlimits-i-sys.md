# RotationLimits（系统接口）

相对于参考点的旋转角度限制

**起始版本：** 20

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## negativePitchMax

```TypeScript
negativePitchMax: number
```

Maximum pitch rotation angles in the negative direction, ranging from -2*Math.PI to 0, measured in radians. If the value is less than or equal to -2*Math.PI, there is no restriction.

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## negativeRollMax

```TypeScript
negativeRollMax: number
```

Maximum roll rotation angles in the negative direction, ranging from -2*Math.PI to 0, measured in radians. If the value is less than or equal to -2*Math.PI, there is no restriction.

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## negativeYawMax

```TypeScript
negativeYawMax: number
```

Maximum yaw rotation angles in the negative direction, ranging from -2*Math.PI to 0, measured in radians. If the value is less than or equal to -2*Math.PI, there is no restriction.

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## positivePitchMax

```TypeScript
positivePitchMax: number
```

Maximum pitch rotation angles in the positive direction, ranging from 0 to 2*Math.PI, measured in radians. If the value is greater than or equal to 2*Math.PI, there is no restriction.

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## positiveRollMax

```TypeScript
positiveRollMax: number
```

Maximum roll rotation angles in the positive direction, ranging from 0 to 2*Math.PI, measured in radians. If the value is greater than or equal to 2*Math.PI, there is no restriction.

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## positiveYawMax

```TypeScript
positiveYawMax: number
```

Maximum yaw rotation angles in the positive direction, ranging from 0 to 2*Math.PI, measured in radians. If the value is greater than or equal to 2*Math.PI, there is no restriction.

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。
