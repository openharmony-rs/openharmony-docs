# SubHeader

```TypeScript
export declare struct SubHeader
```

The **SubHeader** component is used at the top of list items or content items to divide the list or content into sections, with the subtitle name summarizing the content of each section. It supports various style configurations, including icons, primary and secondary titles, dropdown selectors, and operation buttons, meeting content partitioning and navigation needs in different scenarios and enhancing the visual hierarchy and user experience of the UI. It is suitable for list grouping, categorized content display, form partitioning, and other scenarios.

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **SubHeader** component has [universal attributes](../arkts-components/arkts-arkui-common-comp.md) and [universal events](../arkts-components/arkts-arkui-common-comp.md) configured, the compiler toolchain automatically generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node rather than the **SubHeader** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **SubHeader** component.

**Since:** 10

**Decorator:** @Component

<!--Device-unnamed-export declare struct SubHeader--><!--Device-unnamed-export declare struct SubHeader-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { OperationOption, OperationType, SelectOptions, SubHeader, SymbolOptions } from '@kit.ArkUI';
```

## titleBuilder

```TypeScript
titleBuilder?: () => void
```

Custom title area content. When **titleBuilder** is used, title parameters such as **primaryTitle**, **secondaryTitle**, and icon do not take effect.

Default value: **undefined**, indicating that no custom title is used.

**Since:** 12

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SubHeader-titleBuilder?: () => void--><!--Device-SubHeader-titleBuilder?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentMargin

```TypeScript
contentMargin?: LocalizedMargin
```

Margin of the subtitle. Negative values are not supported.

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

<!--Device-SubHeader-contentMargin?: LocalizedMargin--><!--Device-SubHeader-contentMargin?: LocalizedMargin-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentPadding

```TypeScript
contentPadding?: LocalizedPadding
```

Padding of the subtitle. Negative values are not supported.

Default value:

When the left side contains a secondary title or a secondary title with an icon:

`{start: LengthMetrics.vp(12), end: LengthMetrics.vp(12)}`.

**Type:** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**Default:** set different default values according to the width of the subHeader: <br> When the left area is secondaryTitle or the group of secondaryTitle and icon, <br> the default value is {start: LengthMetrics.vp(12), end: LengthMetrics.vp(12)};

**Since:** 12

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SubHeader-contentPadding?: LocalizedPadding--><!--Device-SubHeader-contentPadding?: LocalizedPadding-End-->

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

<!--Device-SubHeader-endIcon?: ResourceStr--><!--Device-SubHeader-endIcon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## endIconSymbolOptions

```TypeScript
endIconSymbolOptions?: SymbolOptions
```

End icon symbol options. This parameter is available when **endIcon** is set to a [symbol glyph](../arkts-components/arkts-arkui-symbolglyph-comp.md). Default value: **undefined**, indicating that no end icon symbol style is set.

**Type:** [SymbolOptions](arkts-arkui-arkui-advanced-subheader-symboloptions-c.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-SubHeader-endIconSymbolOptions?: SymbolOptions--><!--Device-SubHeader-endIconSymbolOptions?: SymbolOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Icon resource.

Default value: **undefined**, indicating that no icon is displayed.

The icon attribute takes effect only when the **secondaryTitle** attribute is used. When the **primaryTitle**, **secondaryTitle**, and **icon** attributes are used together, the **primaryTitle** attribute does not take effect.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SubHeader-icon?: ResourceStr--><!--Device-SubHeader-icon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconSymbolOptions

```TypeScript
iconSymbolOptions?: SymbolOptions
```

Settings when icon is [SymbolGlyph](../arkts-components/arkts-arkui-symbolglyph-comp.md).

Default value: **undefined**, indicating that no icon is displayed.

**Type:** [SymbolOptions](arkts-arkui-arkui-advanced-subheader-symboloptions-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SubHeader-iconSymbolOptions?: SymbolOptions--><!--Device-SubHeader-iconSymbolOptions?: SymbolOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## operationItem

```TypeScript
operationItem?: Array<OperationOption>
```

Settings for the operation area (right side). When **operationType** is **OperationType.ICON_GROUP**, a maximum of three icon items can be configured.

Default value: **undefined**, indicating that no operation area is displayed.

**Type:** Array&lt;[OperationOption](arkts-arkui-arkui-advanced-subheader-operationoption-c.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SubHeader-operationItem?: Array<OperationOption>--><!--Device-SubHeader-operationItem?: Array<OperationOption>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## operationSymbolOptions

```TypeScript
operationSymbolOptions?: Array<SymbolOptions>
```

Settings when **operationType** is **OperationType.ICON_GROUP**, **operationItem** is set with multiple icons, and the icons are [SymbolGlyph](../arkts-components/arkts-arkui-symbolglyph-comp.md).

Default value: **undefined**, indicating that no symbol icon is set.

**Type:** Array&lt;[SymbolOptions](arkts-arkui-arkui-advanced-subheader-symboloptions-c.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SubHeader-operationSymbolOptions?: Array<SymbolOptions>--><!--Device-SubHeader-operationSymbolOptions?: Array<SymbolOptions>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## operationType

```TypeScript
operationType?: OperationType
```

Element style of the operation area (right side).

Default value: **OperationType.BUTTON**

**Type:** [OperationType](arkts-arkui-arkui-advanced-subheader-operationtype-e.md)

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SubHeader-operationType?: OperationType--><!--Device-SubHeader-operationType?: OperationType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
primaryTitle?: ResourceStr
```

Primary title content.

Default value: **undefined**, indicating that no title is displayed.

When the **primaryTitle**, **secondaryTitle**, and **icon** attributes are used together, the **primaryTitle** attribute does not take effect.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SubHeader-primaryTitle?: ResourceStr--><!--Device-SubHeader-primaryTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryTitleModifier

```TypeScript
primaryTitleModifier?: TextModifier
```

Title text attributes, such as title color, font size, font weight, etc.

Default value: **undefined**, indicating that the system default style is used.

**Note:** This parameter takes effect only when **primaryTitle** is effective.

**Type:** [TextModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SubHeader-primaryTitleModifier?: TextModifier--><!--Device-SubHeader-primaryTitleModifier?: TextModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
secondaryTitle?: ResourceStr
```

Secondary title content.

Default value: **undefined**, indicating that no secondary title is displayed. When the **primaryTitle**, **secondaryTitle**, and **icon** attributes are used together, the **primaryTitle** attribute does not take effect.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SubHeader-secondaryTitle?: ResourceStr--><!--Device-SubHeader-secondaryTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitleModifier

```TypeScript
secondaryTitleModifier?: TextModifier
```

Secondary title text attributes, such as title color, font size, font weight, etc.

Default value: **undefined**, indicating that the system default style is used.

**Type:** [TextModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SubHeader-secondaryTitleModifier?: TextModifier--><!--Device-SubHeader-secondaryTitleModifier?: TextModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## select

```TypeScript
select?: SelectOptions
```

Dropdown box content and events.

Default value: **undefined**, indicating that no dropdown box is displayed.

**Type:** [SelectOptions](arkts-arkui-arkui-advanced-subheader-selectoptions-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SubHeader-select?: SelectOptions--><!--Device-SubHeader-select?: SelectOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## titleAccessibilityText

```TypeScript
titleAccessibilityText?: ResourceStr
```

Custom accessibility reading content for the title.

Default value: **undefined**, indicating that no custom reading content is set, and the title content displayed on the component is read by default.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 23

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-SubHeader-titleAccessibilityText?: ResourceStr--><!--Device-SubHeader-titleAccessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## titleId

```TypeScript
titleId?: string
```

Title identifier. Use this parameter when an ID needs to be set for the title. indicating that no title identifier is set. Default value: **undefined**.

**Type:** string

**Since:** 24

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-SubHeader-titleId?: string--><!--Device-SubHeader-titleId?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
