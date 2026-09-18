# BarrierStyle

Defines the ID, direction, and referenced components of a barrier.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction : BarrierDirection
```

Direction of the barrier.

Vertical-direction barriers (including **TOP** and **BOTTOM**) can only serve as the horizontal anchor of a component. If they are used as a vertical anchor, the anchor value will be **0**. Horizontal-direction barriers (including **LEFT** and **RIGHT**) can only serve as the vertical anchor of a component. If they are used as a horizontal anchor, the anchor value will be **0**.

Default value: **BarrierDirection.LEFT**

Invalid values are treated as the default value.

**Type:** [BarrierDirection](arkts-arkui-barrierdirection-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id : string
```

ID of the barrier, which must be unique and cannot be the same as the name of any component in the container.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## referencedId

```TypeScript
referencedId : Array<string>
```

Referenced components of the barrier.

**Type:** Array&lt;string&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
