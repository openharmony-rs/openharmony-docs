# PanGestureHandlerOptions

Provides the parameters of the pan gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md).

**Inheritance/Implementation:** PanGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: PanDirection
```

Pan direction. The value supports the AND (&) and OR (|) operations.

Default value: **PanDirection.All**

**Type:** [PanDirection](arkts-arkui-pandirection-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## distance

```TypeScript
distance?: number
```

Minimum pan distance to trigger the gesture, in vp.

Default value: **8** for the stylus and **5** for other input sources

**NOTE:** 

If a pan gesture and a [tab](../../apis-avsession-kit/arkts-apis/arkts-avsession-avmusictemplate-customelement-i.md#tabs) swipe occur at the same time, set **distance** to **1** to make the gesture more easily recognizable.

Value range: [0, +∞). If the value specified is less than 0, the default value is used.

Since API version 19, the default value is **8**, in vp, for the stylus.

When configuring this field with [gestureModifier](arkts-arkui-commonmethod-c.md#gesturemodifier), the unit is px.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## distanceMap

```TypeScript
distanceMap?: Map<SourceTool, number>
```

Minimum pan distance for different input sources to trigger the gesture, in vp.

Default value: **8** for the stylus and **5** for other input sources

Value range: [0, +∞). If the value specified is less than 0, the default value is used.

**Type:** Map&lt;[SourceTool](arkts-arkui-sourcetool-e.md), number&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: number
```

Minimum number of fingers to trigger a pan gesture. The value ranges from 1 to 10.

Default value: **1**

Value range: [1, 10]

**NOTE:** 

If the value is less than 1 or is not set, the default value is used.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
