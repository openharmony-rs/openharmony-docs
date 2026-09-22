# SubHeader

```TypeScript
export declare struct SubHeader
```

The **SubHeader** component is positioned at the top of list items or content sections, organizing lists or content into distinct groups. The subheader text summarizes the content within each respective section.

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **SubHeader** component has [universal attributes](../arkts-components/arkts-arkui-common-comp.md#common) and [universal events](../arkts-components/arkts-arkui-common-comp.md#common) configured, the compiler toolchain automatically generates an additional **__Common__** node and mounts the universal attributes and universal events on this node rather than the **SubHeader** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **SubHeader** component.

**Since:** 10

**Decorator:** @Component

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { OperationOption, OperationType, SelectOptions, SubHeader, SymbolOptions } from '@kit.ArkUI';
```

## titleBuilder

```TypeScript
titleBuilder?: () => void
```

Content of the custom title area.

Default value: **undefined**, indicating that no custom title is used.

**Since:** 12

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentMargin

```TypeScript
contentMargin?: LocalizedMargin
```

Margin of the content. Negative numbers are not supported.

Default value:

`{start: LengthMetrics.resource(`

`$r('sys.float.margin_left'))`,

`end: LengthMetrics.resource(`

`$r('sys.float.margin_right'))}`

**Type:** [LocalizedMargin](arkts-arkui-localizedmargin-t.md)

**Default:** {start: LengthMetrics.resource($r('sys.float.margin_left')), <br> end: LengthMetrics.resource($r('sys.float.margin_right'))}

**Since:** 12

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentPadding

```TypeScript
contentPadding?: LocalizedPadding
```

Padding of the content.

Default value:

If a secondary title, with or without an icon, is displayed on the left:

{start: LengthMetrics.vp(12), end: LengthMetrics.vp(12)}

**Type:** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**Default:** set different default values according to the width of the subHeader: <br> When the left area is secondaryTitle or the group of secondaryTitle and icon, <br> the default value is {start: LengthMetrics.vp(12), end: LengthMetrics.vp(12)};

**Since:** 12

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## endIcon

```TypeScript
endIcon?: ResourceStr
```

End icon of the title. The **endIcon** attribute takes effect only when the **primaryTitle** or **secondaryTitle** attribute is used. Default value: **undefined**, indicating that no end icon is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.1

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## endIconSymbolOptions

```TypeScript
endIconSymbolOptions?: SymbolOptions
```

End icon symbol options. This parameter is available when **endIcon** is set to a [symbol glyph](../arkts-components/arkts-arkui-symbolglyph-comp.md#symbolglyph).

Default value: **undefined**, indicating that no end icon symbol style is set.

**Type:** [SymbolOptions](arkts-arkui-arkui-advanced-subheader-symboloptions-c.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Icon.

Default value: **undefined**, indicating that no icon is displayed.

The **icon** attribute takes effect only when the **secondaryTitle** attribute is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconSymbolOptions

```TypeScript
iconSymbolOptions?: SymbolOptions
```

Icon symbol options. This parameter is available when **icon** is set to a [symbol glyph](../arkts-components/arkts-arkui-symbolglyph-comp.md#symbolglyph).

Default value: **undefined**, indicating that no icon is displayed.

**Type:** [SymbolOptions](arkts-arkui-arkui-advanced-subheader-symboloptions-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## operationItem

```TypeScript
operationItem?: Array<OperationOption>
```

Items in the operation area (right).

Default value: **undefined**, indicating that the operation area is not displayed.

**Type:** Array&lt;[OperationOption](arkts-arkui-arkui-advanced-subheader-operationoption-c.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## operationSymbolOptions

```TypeScript
operationSymbolOptions?: Array<SymbolOptions>
```

Icon symbol options.

This parameter is available when **operationType** is set to **OperationType.ICON_GROUP** and **operationItem** is set to an array of [symbol glyphs](../arkts-components/arkts-arkui-symbolglyph-comp.md#symbolglyph).

Default value: **undefined**, indicating that no symbol icon is set.

**Type:** Array&lt;[SymbolOptions](arkts-arkui-arkui-advanced-subheader-symboloptions-c.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## operationType

```TypeScript
operationType?: OperationType
```

Style of elements in the operation area (right).

Default value: **OperationType.BUTTON**

**Type:** [OperationType](arkts-arkui-arkui-advanced-subheader-operationtype-e.md)

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
primaryTitle?: ResourceStr
```

Primary title.

Default value: **undefined**, indicating that no primary title is displayed.

When the **primaryTitle**, **secondaryTitle**, and **icon** attributes are used simultaneously, the **primaryTitle** attribute will not take effect.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryTitleModifier

```TypeScript
primaryTitleModifier?: TextModifier
```

Text attributes of the primary title, such as the font color, font size, and font weight.

Default value: **undefined**, indicating that the default style is used.

**Type:** [TextModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
secondaryTitle?: ResourceStr
```

Secondary title.

Default value: **undefined**, indicating that no secondary title is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitleModifier

```TypeScript
secondaryTitleModifier?: TextModifier
```

Text attributes of the secondary title, such as the font color, font size, and font weight.

Default value: **undefined**, indicating that the default style is used.

**Type:** [TextModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## select

```TypeScript
select?: SelectOptions
```

Content and events for selection.

Default value: **undefined**, indicating that no drop-down list is displayed.

**Type:** [SelectOptions](arkts-arkui-arkui-advanced-subheader-selectoptions-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## titleAccessibilityText

```TypeScript
titleAccessibilityText?: ResourceStr
```

Customized content to be read in the title.

Default value: **undefined**.

If the value is **undefined**, the title content displayed by the component is read by default.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 23

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## titleId

```TypeScript
titleId?: string
```

Set the titleId for title.

**Type:** string

**Since:** 24

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
