# FingerInfo

```TypeScript
interface FingerInfo
```

Defines the finger information type.

**Since:** 8

<!--Device-unnamed-interface FingerInfo--><!--Device-unnamed-interface FingerInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getCurrentLocalPosition

```TypeScript
getCurrentLocalPosition?(): Coordinate2D
```

Gets the coordinates of the top-left corner of the current component based on its real-time position.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-FingerInfo-getCurrentLocalPosition?(): Coordinate2D--><!--Device-FingerInfo-getCurrentLocalPosition?(): Coordinate2D-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Coordinate2D](../arkts-apis/arkts-arkui-coordinate2d-i.md) | return the coordinates of the top-left corner of the current component based on its real-time position. |

## displayX

```TypeScript
displayX: number
```

X-coordinate relative to the upper left corner of the screen, in vp.

Value range: [0, +∞)

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-FingerInfo-displayX: number--><!--Device-FingerInfo-displayX: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: number
```

Y-coordinate relative to the upper left corner of the screen, in vp.

Value range: [0, +∞)

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-FingerInfo-displayY: number--><!--Device-FingerInfo-displayY: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: number
```

X-coordinate relative to the upper left corner of the global display, in vp.

Value range: [0, +∞)

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-FingerInfo-globalDisplayX?: number--><!--Device-FingerInfo-globalDisplayX?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: number
```

Y-coordinate relative to the upper left corner of the global display, in vp.

Value range: [0, +∞)

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-FingerInfo-globalDisplayY?: number--><!--Device-FingerInfo-globalDisplayY?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalX

```TypeScript
globalX: number
```

X-coordinate relative to the upper left corner of the application window, in vp.

Value range: [0, +∞)

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-FingerInfo-globalX: number--><!--Device-FingerInfo-globalX: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalY

```TypeScript
globalY: number
```

Y-coordinate relative to the upper left corner of the application window, in vp.

Value range: [0, +∞)

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-FingerInfo-globalY: number--><!--Device-FingerInfo-globalY: number-End-->

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

<!--Device-FingerInfo-hand?: InteractionHand--><!--Device-FingerInfo-hand?: InteractionHand-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id: number
```

Index of the finger, determined by the number of fingers pressed. The first pressed finger is assigned 0, with the index incrementing by one for each subsequent finger.

**NOTE:** 

Indexes for other input sources (mouse: 1001, stylus: 102, mouse wheel: 0, two-finger trackpad slide: 0) are also converted to finger indexes.

Value range: [0, 9)

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-FingerInfo-id: number--><!--Device-FingerInfo-id: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## localX

```TypeScript
localX: number
```

X-coordinate relative to the upper left corner of the current component's original area, in vp.

Value range: [0, +∞)

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-FingerInfo-localX: number--><!--Device-FingerInfo-localX: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## localY

```TypeScript
localY: number
```

Y-coordinate relative to the upper left corner of the current component's original area, in vp.

Value range: [0, +∞)

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-FingerInfo-localY: number--><!--Device-FingerInfo-localY: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
