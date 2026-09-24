# BarrierStyle

```TypeScript
declare interface BarrierStyle
```

Defines the style of a barrier, which is used to define the ID, direction, and dependent components of a barrier. Child components can reference the barrier by its ID as an anchor for alignment and positioning.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction : BarrierDirection
```

Direction of the barrier.

A horizontal barrier line (**TOP**\/**BOTTOM**) can serve only as a vertical directional anchor (**top** or **bottom**) of a component. When it is used as a horizontal directional anchor, its position is treated as **0**. A vertical barrier line (**LEFT**\/**RIGHT**) can serve only as a horizontal directional anchor (**left** or **right**) of a component. When it is used as a vertical directional anchor, its position is treated as **0**.

Default value: **BarrierDirection.LEFT**

Invalid value: processed as the default value.

**Type:** [BarrierDirection](arkts-arkui-relativecontainer-comp-barrierdirection-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id : string
```

ID of the barrier, used to identify the barrier. A child component can reference this barrier as an anchor by this ID. It must be unique and cannot duplicate the name of any component in the container.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## referencedId

```TypeScript
referencedId : Array<string>
```

Components on which the barrier is generated. Put the IDs of the components that serve as the barrier reference into the array. At least one valid component ID is required. IDs that do not exist are ignored. The barrier position is calculated based on the component boundaries: **LEFT** takes the leftmost, **RIGHT** takes the rightmost, **TOP** takes the topmost, and **BOTTOM** takes the bottommost.

**Type:** Array&lt;string&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
