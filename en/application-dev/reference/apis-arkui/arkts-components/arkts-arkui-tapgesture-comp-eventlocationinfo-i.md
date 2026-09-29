# EventLocationInfo

```TypeScript
declare interface EventLocationInfo
```

Provides coordinate information for tap gestures.

**Since:** 20

<!--Device-unnamed-declare interface EventLocationInfo--><!--Device-unnamed-declare interface EventLocationInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getCurrentLocalPosition

```TypeScript
getCurrentLocalPosition?(): Coordinate2D
```

Gets the coordinates of the top-left corner of the current component based on its real-time position.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EventLocationInfo-getCurrentLocalPosition?(): Coordinate2D--><!--Device-EventLocationInfo-getCurrentLocalPosition?(): Coordinate2D-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Coordinate2D](../arkts-apis/arkts-arkui-coordinate2d-i.md) | return the coordinates of the top-left corner of the current component based on its real-time position. |

## displayX

```TypeScript
displayX: number
```

X coordinate relative to the upper left corner of the screen.

Value range: [0, +∞)

Unit: vp

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-EventLocationInfo-displayX: number--><!--Device-EventLocationInfo-displayX: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: number
```

Y coordinate relative to the upper left corner of the screen.

Value range: [0, +∞)

Unit: vp

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-EventLocationInfo-displayY: number--><!--Device-EventLocationInfo-displayY: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: number
```

X coordinate in the coordinate system with the upper left corner of the main screen as the origin.

Unit: vp

Value range: [0, +∞)

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-EventLocationInfo-globalDisplayX?: number--><!--Device-EventLocationInfo-globalDisplayX?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: number
```

Y coordinate in the coordinate system with the upper left corner of the main screen as the origin.

Unit: vp

Value range: [0, +∞)

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-EventLocationInfo-globalDisplayY?: number--><!--Device-EventLocationInfo-globalDisplayY?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX: number
```

X coordinate relative to the upper left corner of the window.

Value range: [0, +∞)

Unit: vp

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-EventLocationInfo-windowX: number--><!--Device-EventLocationInfo-windowX: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY: number
```

Y coordinate relative to the upper left corner of the window.

Value range: [0, +∞)

Unit: vp

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-EventLocationInfo-windowY: number--><!--Device-EventLocationInfo-windowY: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x: number
```

X coordinate relative to the upper left corner of the component.

Value range: [0, +∞)

Unit: vp

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-EventLocationInfo-x: number--><!--Device-EventLocationInfo-x: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y: number
```

Y coordinate relative to the upper left corner of the component.

Value range: [0, +∞)

Unit: vp

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-EventLocationInfo-y: number--><!--Device-EventLocationInfo-y: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
