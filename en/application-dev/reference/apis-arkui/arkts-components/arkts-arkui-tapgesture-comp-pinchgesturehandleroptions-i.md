# PinchGestureHandlerOptions

```TypeScript
interface PinchGestureHandlerOptions extends BaseHandlerOptions
```

Provides the parameters of the pinch gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md).

**Inheritance/Implementation:** PinchGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md)

**Since:** 12

<!--Device-unnamed-interface PinchGestureHandlerOptions extends BaseHandlerOptions--><!--Device-unnamed-interface PinchGestureHandlerOptions extends BaseHandlerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## distance

```TypeScript
distance?: number
```

Minimum recognition distance, in vp. To recognize a pinch gesture more sensitively, set a smaller positive threshold. To reduce the chance of triggering a pinch due to slight movement or accidental touch, set a larger threshold. You are advised to use the default value first and then adjust it based on the component size and interaction sensitivity.

Default value: **5**

Value range: (0, +∞)

**NOTE:** 

If the recognition distance is less than or equal to 0, the default value is used.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PinchGestureHandlerOptions-distance?: number--><!--Device-PinchGestureHandlerOptions-distance?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: number
```

Minimum number of fingers that trigger a pinch. The value ranges from 2 to 5.

Default value: **2**

Value range: [2, 5]

If the value is less than 2 or greater than 5, the default value **2** is used. If **isFingerCountLimited** is not enabled, the number of fingers that trigger the gesture can be greater than **fingers**, but only the first **fingers** fingers that touch the screen participate in gesture calculation. If **isFingerCountLimited** is enabled, the number of fingers touching the screen must be equal to **fingers**; otherwise, the gesture will not be recognized.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PinchGestureHandlerOptions-fingers?: number--><!--Device-PinchGestureHandlerOptions-fingers?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
