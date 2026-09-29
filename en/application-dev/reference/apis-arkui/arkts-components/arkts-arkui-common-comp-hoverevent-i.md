# HoverEvent

```TypeScript
declare interface HoverEvent extends BaseEvent
```

Inherits from [BaseEvent](arkts-arkui-common-comp-baseevent-i.md).

**Inheritance/Implementation:** HoverEvent extends [BaseEvent](arkts-arkui-common-comp-baseevent-i.md)

**Since:** 10

<!--Device-unnamed-declare interface HoverEvent extends BaseEvent--><!--Device-unnamed-declare interface HoverEvent extends BaseEvent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stopPropagation

```TypeScript
stopPropagation: () => void
```

Disables [event bubbling](../../../ui/arkts-interaction-basic-principles.md#event-bubbling) propagation.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HoverEvent-stopPropagation: () => void--><!--Device-HoverEvent-stopPropagation: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayX

```TypeScript
displayX?: number
```

X coordinate of the cursor or stylus position in the coordinate system of the current screen window.

Unit: vp.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-HoverEvent-displayX?: number--><!--Device-HoverEvent-displayX?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY?: number
```

Y coordinate of the cursor or stylus position in the coordinate system of the current screen window.

Unit: vp.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-HoverEvent-displayY?: number--><!--Device-HoverEvent-displayY?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: number
```

X coordinate of the cursor or stylus position in the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system).

Unit: vp.

Value range: (-∞, +∞).

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-HoverEvent-globalDisplayX?: number--><!--Device-HoverEvent-globalDisplayX?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: number
```

Y coordinate of the cursor or stylus position in the [global coordinate system](../../../windowmanager/window-terminology.md#global-coordinate-system).

Unit: vp.

Value range: (-∞, +∞).

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-HoverEvent-globalDisplayY?: number--><!--Device-HoverEvent-globalDisplayY?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX?: number
```

X coordinate of the cursor or stylus position in the coordinate system of the current application window.

Unit: vp.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-HoverEvent-windowX?: number--><!--Device-HoverEvent-windowX?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY?: number
```

Y coordinate of the cursor or stylus position in the coordinate system of the current application window.

Unit: vp.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-HoverEvent-windowY?: number--><!--Device-HoverEvent-windowY?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: number
```

X coordinate of the cursor or stylus position in the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system) based on the current component.

Unit: vp.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-HoverEvent-x?: number--><!--Device-HoverEvent-x?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: number
```

Y coordinate of the cursor or stylus position in the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system) based on the current component.

Unit: vp.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-HoverEvent-y?: number--><!--Device-HoverEvent-y?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
