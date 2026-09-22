# LocalizedBarrierStyle

```TypeScript
declare interface LocalizedBarrierStyle
```

Defines the style of a localized barrier, which is used to define the ID, direction, and dependent components of a barrier that supports mirror mode. Child components can reference the barrier by its ID as an anchor for alignment and positioning.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id : string
```

ID of the barrier, used to identify the barrier. A child component can reference this ID to use the barrier as an anchor. The ID must be unique and must not duplicate the name of any component in the container.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## localizedDirection

```TypeScript
localizedDirection : LocalizedBarrierDirection
```

Direction of the barrier.

A horizontal barrier line (**TOP**\/**BOTTOM**) can be used only as a vertical directional anchor (**top** or **bottom**) of a component. When it is used as a horizontal directional anchor, its position is treated as **0**. A vertical barrier line (**START**\/**END**, supporting LTR/RTL mirroring) can be used only as a horizontal directional anchor (**start** or **end**) of a component. When it is used as a vertical directional anchor, its position is treated as **0**.

Default value: **LocalizedBarrierDirection.START**

Invalid value: the default value is used.

**Type:** [LocalizedBarrierDirection](arkts-arkui-relativecontainer-comp-localizedbarrierdirection-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## referencedId

```TypeScript
referencedId : Array<string>
```

Components on which the barrier is generated. Put the IDs of the components that serve as the barrier reference into the array. The array must contain at least one valid component ID. IDs that do not exist are ignored. For a barrier that supports mirror mode, the barrier position is calculated based on the actual position in LTR/RTL mode.

**Type:** Array&lt;string&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
