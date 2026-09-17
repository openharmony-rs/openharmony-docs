# RotationGestureHandlerOptions

Provides the parameters of the rotation gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md).

**Inheritance/Implementation:** RotationGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle?: number
```

Minimum angle change required to trigger the rotation gesture, in degrees (deg).

Default value: **1**

**NOTE:** 

If the value is less than or equal to 0 or greater than 360, it will be converted to the default value.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: number
```

Minimum number of fingers required to trigger the rotation gesture. The value ranges from 2 to 5.

Default value: **2**

Value range: [2, 5]

While more fingers than the minimum number can be pressed to trigger the gesture, only the first two fingers participate in gesture calculation.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
