# GuideLineStyle

Defines the ID, direction, and position of a guideline.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction : Axis
```

Direction of the guideline.

A guideline in the vertical direction can only be used as the anchor of the component in the horizontal direction, and the value is **0** when it is used as the anchor in the vertical direction. A guideline in the horizontal direction can only be used as the anchor of the component in the vertical direction, and the value is **0** when it is used as the anchor in the horizontal direction.

Default value: **Axis.Vertical**

Invalid values are treated as the default value.

**Type:** [Axis](../arkts-apis/arkts-arkui-axis-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id : string
```

ID of the guideline, which must be unique and cannot be the same as the name of any component in the container.

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

If no value is specified or an invalid value (for example, **undefined**) is provided, the guideline position defaults to **start: 0**. Only **start** or **end** can be selected for the guideline position. If both are declared, only **start** takes effect. If the container size in a certain direction is set to **"auto"**, the guideline position in that direction must be declared in **start** mode, and the value cannot be a percentage.

Default value:  
```
{
 start: 0
}
``` 

Invalid values are treated as the default value.

**Type:** [GuideLinePosition](arkts-arkui-guidelineposition-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
