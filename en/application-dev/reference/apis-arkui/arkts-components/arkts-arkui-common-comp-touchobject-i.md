# TouchObject

```TypeScript
declare interface TouchObject
```

Type of the touch event.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getCurrentLocalPosition

```TypeScript
getCurrentLocalPosition?(): Coordinate2D
```

Gets the coordinates of the top-left corner of the current component based on its real-time position.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Coordinate2D](../arkts-apis/arkts-arkui-coordinate2d-i.md) | return the coordinates of the top-left corner of the current component based on its real-time position. |

## displayX

```TypeScript
displayX: number
```

X coordinate of the touch point in the coordinate system of the current application screen.

Unit: vp.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: number
```

Y coordinate of the touch point in the coordinate system of the current application screen.

Unit: vp.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: number
```

X coordinate of the touch point in the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system).

Unit: vp.

Value range: (-∞, +∞).

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: number
```

Y coordinate of the touch point in the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system).

Unit: vp.

Value range: (-∞, +∞).

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hand

```TypeScript
hand?: InteractionHand
```

Whether the event was triggered by a left-hand or right-hand tap.

**Type:** [InteractionHand](../arkts-apis/arkts-arkui-interactionhand-e.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: number
```

Height of the finger contact area.

Unit: vp.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id: number
```

Unique identifier of a finger.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pressedTime

```TypeScript
pressedTime?: number
```

Time when the finger is pressed.

Unit: ns

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pressure

```TypeScript
pressure?: number
```

Pressure value of finger contact.

Value range: [0, 65535), where higher values indicate stronger pressure.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## screenX

```TypeScript
screenX: number
```

X coordinate of the touch point in the coordinate system of the current application window.

Unit: vp.

Note: This API is supported since API version 7 and deprecated since API version 10. You are advised to use **windowX** instead.

**Type:** number

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [windowX](#windowx)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## screenY

```TypeScript
screenY: number
```

Y coordinate of the touch point in the coordinate system of the current application window.

Unit: vp.

Note: This API is supported since API version 7 and deprecated since API version 10. You are advised to use **windowY** instead.

**Type:** number

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [windowY](#windowy)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: TouchType
```

Type of the touch event.

**Type:** [TouchType](../arkts-apis/arkts-arkui-touchtype-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: number
```

Width of the finger contact area.

Unit: vp.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX: number
```

X coordinate of the touch point in the coordinate system of the current application window.

Unit: vp.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY: number
```

Y coordinate of the touch point in the coordinate system of the current application window.

Unit: vp.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x: number
```

X coordinate of the touch point in the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system) based on the event- responsive component.

Unit: vp.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y: number
```

Y coordinate of the touch point in the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system) based on the event- responsive component.

Unit: vp.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
