# MouseEvent

```TypeScript
declare interface MouseEvent extends BaseEvent
```

Inherits from [BaseEvent](arkts-arkui-common-comp-baseevent-i.md).

**Inheritance/Implementation:** MouseEvent extends [BaseEvent](arkts-arkui-common-comp-baseevent-i.md)

**Since:** 8

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

## getHistoricalPoints

```TypeScript
getHistoricalPoints?(): Array<MouseHistoricalPoint>
```

Obtains all historical point information of the current frame. Historical points can be used to achieve smoother drawing effects.

This API can only be called from [MouseEvent](arkts-arkui-common-comp-mouseevent-i.md) to obtain information about historical points of the current frame when [onMouse](arkts-arkui-common-comp-commonmethod-c.md#onmouse) is triggered. The mouse event reporting frequency per frame varies across different devices. Typically, only one mouse event is reported per frame. If the number of [MouseEvent](arkts-arkui-common-comp-mouseevent-i.md) instances received in the current frame is greater than 1, the last point of that frame is returned via [onMouse](arkts-arkui-common-comp-commonmethod-c.md#onmouse), and the remaining points are treated as historical points.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[MouseHistoricalPoint](arkts-arkui-common-comp-mousehistoricalpoint-i.md)&gt; | Array of all historical point information for the current frame. |

## stopPropagation

```TypeScript
stopPropagation: () => void
```

Disables [event bubbling](../../../ui/arkts-interaction-basic-principles.md#event-bubbling) propagation.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: MouseAction
```

Mouse action.

**Type:** [MouseAction](../arkts-apis/arkts-arkui-mouseaction-e.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## button

```TypeScript
button: MouseButton
```

Mouse button.

**Type:** [MouseButton](../arkts-apis/arkts-arkui-mousebutton-e.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayX

```TypeScript
displayX: number
```

X coordinate of the mouse position in the coordinate system of the current screen window.

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

Y coordinate of the mouse position in the coordinate system of the current screen window.

Unit: vp.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## eventHandleId

```TypeScript
eventHandleId?: number
```

Unique identifier for event processing.

Value range: [0, +∞)

**NOTE:** 

This field is used when dispatching events using the [postInputEventWithStrategy](../arkts-apis/arkts-arkui-buildernode-c.md#postinputeventwithstrategy) API. Each time an event is dispatched, this field is increased by 100000.

Using the same **eventHandleId** for multiple event dispatches will cause abnormal event responses. This field only needs to be assigned when constructing an event; developers do not need to handle it in other cases.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: number
```

X coordinate of the mouse position in the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system).

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

Y coordinate of the mouse position in the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system).

Unit: vp.

Value range: (-∞, +∞).

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pressedButtons

```TypeScript
pressedButtons?: MouseButton[]
```

Set of buttons being pressed.

**Type:** [MouseButton](../arkts-apis/arkts-arkui-mousebutton-e.md)[]

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rawDeltaX

```TypeScript
rawDeltaX?: number
```

Movement increment of the mouse along the X axis in a two-dimensional plane. The value is the original movement data of the mouse hardware, which is expressed in the unit of the mouse movement distance in the physical world. The reported value is determined by the hardware, not the physical or logical pixels of the screen.

**NOTE:** 

Before API version 26.0.0, the return value of **rawDeltaX** was not the original movement data of the mouse hardware, but the original data reduced by a factor of X, where X is the system's display size ratio. Since API version 26.0.0, the return value of **rawDeltaX** is the original movement data of the mouse hardware.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rawDeltaY

```TypeScript
rawDeltaY?: number
```

Movement increment of the mouse along the Y axis in a two-dimensional plane. The value is the original movement data of the mouse hardware, which is expressed in the unit of the mouse movement distance in the physical world. The reported value is determined by the hardware, not the physical or logical pixels of the screen.

**NOTE:** 

Before API version 26.0.0, the return value of **rawDeltaY** was not the original movement data of the mouse hardware, but the original data reduced by a factor of X, where X is the system's display size ratio. Since API version 26.0.0, the return value of **rawDeltaY** is the original movement data of the mouse hardware.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## screenX

```TypeScript
screenX: number
```

X coordinate of the mouse position in the coordinate system of the current application window.

Unit: vp.

Note: This API is supported since API version 8 and deprecated since API version 10. You are advised to use **windowX** instead.

**Type:** number

**Since:** 8

**Deprecated since:** 10

**Substitutes:** [windowX](#windowx)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## screenY

```TypeScript
screenY: number
```

Y coordinate of the mouse position in the coordinate system of the current application window.

Unit: vp.

Note: This API is supported since API version 8 and deprecated since API version 10. You are advised to use **windowY** instead.

**Type:** number

**Since:** 8

**Deprecated since:** 10

**Substitutes:** [windowY](#windowy)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX: number
```

X coordinate of the mouse position in the coordinate system of the current application window.

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

Y coordinate of the mouse position in the coordinate system of the current application window.

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

X coordinate of the mouse point in the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system) based on the event- responsive component.

Unit: vp.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y: number
```

Y coordinate of the mouse point in the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system) based on the event- responsive component.

Unit: vp.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
