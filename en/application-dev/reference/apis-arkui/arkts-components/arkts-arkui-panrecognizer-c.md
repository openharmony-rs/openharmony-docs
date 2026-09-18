# PanRecognizer

Gesture recognizer object.

**Inheritance/Implementation:** PanRecognizer extends [GestureRecognizer](arkts-arkui-gesturerecognizer-c.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getDirection

```TypeScript
getDirection(): PanDirection
```

Obtains the recognized direction of the current pan gesture recognizer.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [PanDirection](arkts-arkui-pandirection-e.md) | Recognized direction of the current pan gesture recognizer. |

## getDistance

```TypeScript
getDistance(): number
```

Obtains the minimum pan distance required to trigger this pan gesture recognizer.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Minimum swipe distance. Unit: vp. |

## getDistanceMap

```TypeScript
getDistanceMap(): Map<SourceTool, number>
```

Obtains the minimum pan distances required for different input sources to trigger this pan gesture recognizer.

> **NOTE:** 
> 
> This API only returns thresholds for input sources that have been explicitly configured during pan gesture
> initialization. The default threshold can be queried using the [SourceTool](arkts-arkui-sourcetool-e.md).Unknown type.
> Thresholds for unconfigured device types are not available.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Map&lt;[SourceTool](arkts-arkui-sourcetool-e.md), number&gt; | Minimum pan distances required for different input sources to trigger the pan gesture recognizer. Unit: vp. |

## getPanGestureOptions

```TypeScript
getPanGestureOptions(): PanGestureOptions
```

Obtains the properties of this pan gesture recognizer.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureOptions](arkts-arkui-pangestureoptions-c.md) | Properties of the current pan gesture recognizer. |
