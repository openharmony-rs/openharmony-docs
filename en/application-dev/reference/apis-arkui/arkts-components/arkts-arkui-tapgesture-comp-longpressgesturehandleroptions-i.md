# LongPressGestureHandlerOptions

```TypeScript
interface LongPressGestureHandlerOptions extends BaseHandlerOptions
```

Provides the parameters of the long press gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md).

**Inheritance/Implementation:** LongPressGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md)

**Since:** 12

<!--Device-unnamed-interface LongPressGestureHandlerOptions extends BaseHandlerOptions--><!--Device-unnamed-interface LongPressGestureHandlerOptions extends BaseHandlerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## allowableMovement

```TypeScript
allowableMovement?: number
```

Maximum movement distance recognized by the long press gesture recognizer, in px.

Default value: **15**

Value range: (0, +∞). If the value is less than or equal to 0, the default value **15** is used.

**Type:** number

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-LongPressGestureHandlerOptions-allowableMovement?: number--><!--Device-LongPressGestureHandlerOptions-allowableMovement?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

Minimum hold-down time, in ms.

Default value: **500**

**NOTE:** 

Value range: (0, +∞). If the value is less than or equal to 0, the default value **500** is used.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LongPressGestureHandlerOptions-duration?: number--><!--Device-LongPressGestureHandlerOptions-duration?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: number
```

Minimum number of fingers to trigger a long press. When **isFingerCountLimited** is enabled, the number of fingers touching the screen must equal the fingers value; otherwise, gesture recognition fails.

Default value: **1**

Value range: [1, 10]

**NOTE:** 

If a finger moves more than 15 px after being pressed, the gesture recognition fails.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LongPressGestureHandlerOptions-fingers?: number--><!--Device-LongPressGestureHandlerOptions-fingers?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## repeat

```TypeScript
repeat?: boolean
```

Whether to continuously trigger the event callback. The value **true** means to continuously trigger the event callback, and **false** means the opposite.

Default value: **false**

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LongPressGestureHandlerOptions-repeat?: boolean--><!--Device-LongPressGestureHandlerOptions-repeat?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
