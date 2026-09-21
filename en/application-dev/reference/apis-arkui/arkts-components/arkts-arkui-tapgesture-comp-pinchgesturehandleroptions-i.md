# PinchGestureHandlerOptions

```TypeScript
interface PinchGestureHandlerOptions extends BaseHandlerOptions
```

Provides the parameters of the pinch gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md).

**Inheritance/Implementation:** PinchGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## distance

```TypeScript
distance?: number
```

Minimum recognition distance, in vp.

Default value: **5**

**NOTE:** 

If the value is less than or equal to 0, it will be converted to the default value.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: number
```

Minimum number of fingers required to trigger the pinch gesture. The value ranges from 2 to 5.

Default value: **2**

Value range: [2, 5]

While more fingers than the minimum number can be pressed to trigger the gesture, only the first fingers of the minimum number participate in gesture calculation.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
