# PanRecognizer

```TypeScript
declare class PanRecognizer extends GestureRecognizer
```

Defines the pan gesture recognizer object, which inherits from [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md) and supports querying pan gesture attributes, recognition direction, minimum pan distance, and pan thresholds for different input sources. It is applicable to querying the pan gesture recognition configuration.

**Inheritance/Implementation:** PanRecognizer extends [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md)

**Since:** 12

<!--Device-unnamed-declare class PanRecognizer extends GestureRecognizer--><!--Device-unnamed-declare class PanRecognizer extends GestureRecognizer-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getDirection

```TypeScript
getDirection(): PanDirection
```

Obtains the recognized direction of the current pan gesture recognizer.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-PanRecognizer-getDirection(): PanDirection--><!--Device-PanRecognizer-getDirection(): PanDirection-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [PanDirection](arkts-arkui-tapgesture-comp-pandirection-e.md) | Recognized direction of the current pan gesture recognizer. |

## getDistance

```TypeScript
getDistance(): number
```

Returns the minimum pan distance that triggers the current pan gesture recognizer. The default pan threshold is 5 vp.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-PanRecognizer-getDistance(): number--><!--Device-PanRecognizer-getDistance(): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Minimum pan distance that triggers the current pan gesture recognizer. If the minimum pan distance is not configured, the default pan threshold 5vp is returned. Unit: vp |

## getDistanceMap

```TypeScript
getDistanceMap(): Map<SourceTool, number>
```

Returns the minimum pan distance that triggers the pan gesture recognizer for different input sources. The default pan threshold is 5 vp.

> **NOTE:** 
> 
> This API only returns thresholds for input sources that have been explicitly configured during pan gesture
> initialization. The default threshold can be queried using the [SourceTool](arkts-arkui-common-comp-sourcetool-e.md).Unknown type.
> Thresholds for unconfigured device types are not available.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-PanRecognizer-getDistanceMap(): Map<SourceTool, number>--><!--Device-PanRecognizer-getDistanceMap(): Map<SourceTool, number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Map&lt;[SourceTool](arkts-arkui-common-comp-sourcetool-e.md), number&gt; | Minimum pan distances required for different input sources to trigger the pan gesture recognizer. Unit: vp. |

## getPanGestureOptions

```TypeScript
getPanGestureOptions(): PanGestureOptions
```

Obtains the properties of this pan gesture recognizer.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PanRecognizer-getPanGestureOptions(): PanGestureOptions--><!--Device-PanRecognizer-getPanGestureOptions(): PanGestureOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureOptions](arkts-arkui-tapgesture-comp-pangestureoptions-c.md) | Properties of the current pan gesture recognizer. |
