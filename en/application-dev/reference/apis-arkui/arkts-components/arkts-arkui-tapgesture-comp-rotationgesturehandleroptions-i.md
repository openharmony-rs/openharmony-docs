# RotationGestureHandlerOptions

```TypeScript
interface RotationGestureHandlerOptions extends BaseHandlerOptions
```

Provides the parameters of the rotation gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md).

**Inheritance/Implementation:** RotationGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md)

**Since:** 12

<!--Device-unnamed-interface RotationGestureHandlerOptions extends BaseHandlerOptions--><!--Device-unnamed-interface RotationGestureHandlerOptions extends BaseHandlerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle?: number
```

Minimum angle change required to trigger the rotation gesture, in degrees (deg). To recognize slight rotations more sensitively, set a smaller positive angle. To reduce accidental touches or respond only to obvious rotations, set a larger angle. It is recommended to use the default value first and then adjust it based on the rotation interaction precision requirements.

Default value: **1**

Value range: (0, 360]

**NOTE:** 

If the value is less than or equal to 0 or greater than 360, it will be converted to the default value.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RotationGestureHandlerOptions-angle?: number--><!--Device-RotationGestureHandlerOptions-angle?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: number
```

Minimum number of fingers required to trigger rotation. The minimum is 2 and the maximum is 5.

Default value: **2**

Value range: [2, 5]

If the value is less than 2 or greater than 5, the default value **2** is used. When **isFingerCountLimited** is not enabled, the number of fingers touching the screen can be greater than the value of **fingers** when the gesture is triggered, but only the first two fingers that touch the screen participate in gesture calculation. When **isFingerCountLimited** is enabled, the number of fingers touching the screen must be equal to the value of **fingers**; otherwise, the gesture will not be recognized.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RotationGestureHandlerOptions-fingers?: number--><!--Device-RotationGestureHandlerOptions-fingers?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
