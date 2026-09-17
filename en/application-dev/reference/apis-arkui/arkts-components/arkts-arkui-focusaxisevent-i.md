# FocusAxisEvent

Describes the focus axis event object. Inherits from [BaseEvent](arkts-arkui-baseevent-i.md).

**Inheritance/Implementation:** FocusAxisEvent extends [BaseEvent](arkts-arkui-baseevent-i.md)

**Since:** 15

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## axisMap

```TypeScript
axisMap: Map<AxisModel, number>
```

Axis value table of the focus axis event.

**Type:** Map&lt;[AxisModel](../arkts-apis/arkts-arkui-axismodel-e.md), number&gt;

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stopPropagation

```TypeScript
stopPropagation: Callback<void>
```

Blocks [event bubbling](../../../ui/arkts-interaction-basic-principles.md#event-bubbling) propagation.

**Type:** [Callback](arkts-arkui-callback-i.md)&lt;void&gt;

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
