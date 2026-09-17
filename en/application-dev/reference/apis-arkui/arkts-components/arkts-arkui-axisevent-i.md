# AxisEvent

Describes the axis event object. Inherits from [BaseEvent](arkts-arkui-baseevent-i.md).

**Inheritance/Implementation:** AxisEvent extends [BaseEvent](arkts-arkui-baseevent-i.md)

**Since:** 17

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

## getHorizontalAxisValue

```TypeScript
getHorizontalAxisValue(): number
```

Obtains the horizontal axis value of this axis event.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Horizontal axis value.<br>Unit: vp |

## getPinchAxisScaleValue

```TypeScript
getPinchAxisScaleValue(): number
```

Obtains the two-finger pinch zoom ratio from the axis event.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Two-finger pinch zoom ratio.<br> Note: This ratio is calculated as the current distance between two fingers during a touchpad pinch event divided by the initial distance when the fingers first made contact. <br>Default value: **0**. <br>Value range: [0, +∞). <br> |

## getVerticalAxisValue

```TypeScript
getVerticalAxisValue(): number
```

Obtains the vertical axis value of this axis event.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Vertical axis value.<br>Unit: vp |

## hasAxis

```TypeScript
hasAxis(axisType: AxisType): boolean
```

Checks whether this axis event contains the specified axis type.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| axisType | [AxisType](../arkts-apis/arkts-arkui-axistype-e.md) | Yes | Axis type to check for. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the axis event contains the specified axis type.<br>**true** if the axis event contains the specified axis type; **false** otherwise. |

## action

```TypeScript
action: AxisAction
```

Action type of the axis event.

**Type:** [AxisAction](../arkts-apis/arkts-arkui-axisaction-e.md)

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayX

```TypeScript
displayX: number
```

X coordinate of the cursor in the coordinate system of the current application screen.

Unit: vp

**Type:** number

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: number
```

Y coordinate of the cursor in the coordinate system of the current application screen.

Unit: vp

**Type:** number

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

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

X coordinate of the cursor in the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system).

Unit: vp

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

Y coordinate of the cursor in the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system).

Unit: vp

Value range: (-∞, +∞).

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## propagation

```TypeScript
propagation: Callback<void>
```

Enables [event bubbling](../../../ui/arkts-interaction-basic-principles.md#event-bubbling) propagation.

**Type:** [Callback](arkts-arkui-callback-i.md)&lt;void&gt;

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scrollStep

```TypeScript
scrollStep?: number
```

Scroll step length for the mouse wheel.

Note: Only the mouse wheel is supported. The value ranges from 0 to 65535.

**Type:** number

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX: number
```

X coordinate of the cursor in the coordinate system of the current application window.

Unit: vp

**Type:** number

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY: number
```

Y coordinate of the cursor in the coordinate system of the current application window.

Unit: vp

**Type:** number

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x: number
```

X coordinate of the cursor in the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system) based on the clicked element.

Unit: vp

**Type:** number

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y: number
```

Y coordinate of the cursor in the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system) based on the clicked element.

Unit: vp

**Type:** number

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
