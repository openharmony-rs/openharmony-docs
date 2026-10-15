# ClickEvent

```TypeScript
declare interface ClickEvent extends BaseEvent
```

Inherits from [BaseEvent](arkts-arkui-common-comp-baseevent-i.md).

**Inheritance/Implementation:** ClickEvent extends [BaseEvent](arkts-arkui-common-comp-baseevent-i.md)

**Since:** 7

<!--Device-unnamed-declare interface ClickEvent extends BaseEvent--><!--Device-unnamed-declare interface ClickEvent extends BaseEvent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getCurrentLocalPosition

```TypeScript
getCurrentLocalPosition?(): Coordinate2D
```

Obtains the coordinates of the click position relative to the upper-left corner of the current component's real-time position. It is suitable for scenarios where the coordinates of the click point relative to the component's current position need to be obtained after the component has been displaced, animated, or its layout has changed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ClickEvent-getCurrentLocalPosition?(): Coordinate2D--><!--Device-ClickEvent-getCurrentLocalPosition?(): Coordinate2D-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Coordinate2D](../arkts-apis/arkts-arkui-coordinate2d-i.md) | Coordinates of the click position relative to the upper left corner of the current component's real-time position. |

## preventDefault

```TypeScript
preventDefault: () => void
```

Blocks the default event.

Note: This API is only supported by the following components: **RichEditor** and **Hyperlink**. An exception is thrown when this API is used with unsupported components. Currently, asynchronous calls and Modifier APIs are not supported.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ClickEvent-preventDefault: () => void--><!--Device-ClickEvent-preventDefault: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100017](../errorcode-event.md#100017-component-does-not-support-default-event-prevention) | Component does not support prevent function. |

## displayX

```TypeScript
displayX: number
```

X coordinate of the click position in the coordinate system of the current application screen. After distanceThreshold is set for **onClick**, the click position is the lift-off point.

Unit: vp

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ClickEvent-displayX: number--><!--Device-ClickEvent-displayX: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: number
```

Y coordinate of the click position in the coordinate system of the current application screen. After distanceThreshold is set for **onClick**, the click position is the lift-off point.

Unit: vp

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ClickEvent-displayY: number--><!--Device-ClickEvent-displayY: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: number
```

X coordinate of the click position in the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system).

Unit: vp

Value range: (-∞, +∞).

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ClickEvent-globalDisplayX?: number--><!--Device-ClickEvent-globalDisplayX?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: number
```

Y coordinate of the click position in the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system).

Unit: vp

Value range: (-∞, +∞).

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ClickEvent-globalDisplayY?: number--><!--Device-ClickEvent-globalDisplayY?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hand

```TypeScript
hand?: InteractionHand
```

Whether the event is triggered by a left-hand or right-hand tap.

**Type:** [InteractionHand](../arkts-apis/arkts-arkui-interactionhand-e.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ClickEvent-hand?: InteractionHand--><!--Device-ClickEvent-hand?: InteractionHand-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX: number
```

X coordinate of the click position in the coordinate system of the current application window. After distanceThreshold is set for **onClick**, the click position is the lift-off point.

Unit: vp

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ClickEvent-windowX: number--><!--Device-ClickEvent-windowX: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY: number
```

Y coordinate of the click position in the coordinate system of the current application window. After distanceThreshold is set for **onClick**, the click position is the lift-off point.

Unit: vp

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ClickEvent-windowY: number--><!--Device-ClickEvent-windowY: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x: number
```

X coordinate of the click position in the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system) based on the clicked element. After [distanceThreshold](arkts-arkui-common-comp-commonmethod-c.md#onclick2) is set for **onClick**, the click position is the lift-off point. If the event is triggered by a keyboard or gamepad device, the click position is the center of the clicked element.

Unit: vp

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ClickEvent-x: number--><!--Device-ClickEvent-x: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y: number
```

Y coordinate of the click position in the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system) based on the clicked element. After distanceThreshold is set for **onClick**, the click position is the lift-off point. If the event is triggered by a keyboard or gamepad device, the click position is the center of the clicked element.

Unit: vp

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ClickEvent-y: number--><!--Device-ClickEvent-y: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## screenX

```TypeScript
screenX: number
```

X coordinate of the click position in the coordinate system of the current application window.

Unit: vp

Note: This API is supported since API version 7 and deprecated since API version 10. You are advised to use **windowX** instead.

**Type:** number

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [windowX](#windowx)

<!--Device-ClickEvent-screenX: number--><!--Device-ClickEvent-screenX: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## screenY

```TypeScript
screenY: number
```

Y coordinate of the click position in the coordinate system of the current application window.

Unit: vp

Note: This API is supported since API version 7 and deprecated since API version 10. You are advised to use **windowY** instead.

**Type:** number

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [windowY](#windowy)

<!--Device-ClickEvent-screenY: number--><!--Device-ClickEvent-screenY: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
