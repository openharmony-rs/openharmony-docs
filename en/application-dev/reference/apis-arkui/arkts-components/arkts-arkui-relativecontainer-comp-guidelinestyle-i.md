# GuideLineStyle

```TypeScript
declare interface GuideLineStyle
```

Defines the style of a guideline, which used to define the ID, direction, and position of a guideline, helping child components to be positioned and aligned in the **RelativeContainer**.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction : Axis
```

Direction of the guideline. **Axis.Vertical** indicates a vertical guideline, which can be used only as a horizontal anchor of a component. **Axis.Horizontal** indicates a horizontal guide line, which can be used only as a vertical anchor of a component.

Default value: **Axis.Vertical**

Invalid value: The default value is used.

**Type:** [Axis](../arkts-apis/arkts-arkui-axis-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id : string
```

ID of the guideline, used to identify the guideline. A child component can reference this guideline as an anchor by using this ID. The ID must be unique and cannot be the same as the name of any component in the container.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position : GuideLinePosition
```

Position of the guideline.

If this parameter is not declared or an invalid value (for example, **undefined**) is declared, the position of the guideline defaults to **start: 0**. You can declare either **start** or **end**. If both are declared, only **start** takes effect. If the width of the container is declared as **"auto"**, the position of an **Axis.Vertical** guideline can be declared only by using **start** (percentages are not allowed). If the **height** of the container is declared as **"auto"**, the position of an **Axis.Horizontal** guideline can be declared only by using **start** (percentages are not allowed).

Default value: **{ start: 0 }**

Invalid value: The default value is used.

**Type:** [GuideLinePosition](arkts-arkui-relativecontainer-comp-guidelineposition-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
