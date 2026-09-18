# CrownEvent

Defines a data structure for the crown event received by a component. It includes the timestamp, angular velocity, rotation angle, crown action, and event propagation disabling.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: CrownAction
```

Crown action.

**Type:** [CrownAction](../arkts-apis/arkts-arkui-crownaction-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## angularVelocity

```TypeScript
angularVelocity: number
```

Angular velocity.

Unit: deg/s

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## degree

```TypeScript
degree: number
```

Relative rotation angle.

Unit: deg

Value range: [-360, 360]

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stopPropagation

```TypeScript
stopPropagation: Callback<void>
```

Disables [event bubbling](../../../ui/arkts-interaction-basic-principles.md#event-bubbling) propagation.

**Type:** [Callback](arkts-arkui-callback-i.md)&lt;void&gt;

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timestamp

```TypeScript
timestamp: number
```

Timestamp.

Unit: ns

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
