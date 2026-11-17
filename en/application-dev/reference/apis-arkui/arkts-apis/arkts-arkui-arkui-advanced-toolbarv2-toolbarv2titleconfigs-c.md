# ToolBarV2TitleConfigs

```TypeScript
export declare class ToolBarV2TitleConfigs
```

标题配置。如果不提供，则不会渲染标题。

标题参与布局，与工具栏项处于同一级别。标题重用ToolBarV2ItemPlacement来确定渲染区域，并与具有相同位置的项目排列在同一区域。

**Since:** 26.1.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class ToolBarV2TitleConfigs--><!--Device-unnamed-export declare class ToolBarV2TitleConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolBarV2Item, AdvancedToolBarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolBarV2ItemGroupStyle, ToolBarV2ItemGroupStyleOptions, ToolBarV2ItemPlacement, ToolBarV2OverflowMenuStyle, ToolBarV2PaddingOptions, ToolBarV2StyleConfigs, ToolBarV2StyleOptions, ToolBarV2TitleConfigs, ToolBarV2TitleOptions, ToolBarV2TitleStyle, ToolBarV2TitleStyleOptions, ToolBarV2MaterialStyle } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ToolBarV2TitleOptions)
```

构造ToolBarV2TitleConfigs实例。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2TitleConfigs-constructor(options?: ToolBarV2TitleOptions)--><!--Device-ToolBarV2TitleConfigs-constructor(options?: ToolBarV2TitleOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ToolBarV2TitleOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2titleoptions-i.md) | No | 构造函数选项。 |

## content

```TypeScript
content: ResourceStr
```

标题文本内容。在构造ToolBarV2TitleConfigs时需要。默认值：undefined。不设置时，无内容。

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2TitleConfigs-content: ResourceStr--><!--Device-ToolBarV2TitleConfigs-content: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placement

```TypeScript
placement?: ToolBarV2ItemPlacement
```

标题位置。默认值：ToolBarV2ItemPlacement.LEADING。

**Type:** [ToolBarV2ItemPlacement](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemplacement-e.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2TitleConfigs-placement?: ToolBarV2ItemPlacement--><!--Device-ToolBarV2TitleConfigs-placement?: ToolBarV2ItemPlacement-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: ToolBarV2TitleStyle
```

标题文字样式。

**Type:** [ToolBarV2TitleStyle](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2titlestyle-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2TitleConfigs-style?: ToolBarV2TitleStyle--><!--Device-ToolBarV2TitleConfigs-style?: ToolBarV2TitleStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## subTitleContent

```TypeScript
subTitleContent?: ResourceStr
```

副标题文本内容。默认值：undefined。不设置时，无内容。

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2TitleConfigs-subTitleContent?: ResourceStr--><!--Device-ToolBarV2TitleConfigs-subTitleContent?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## subTitleStyle

```TypeScript
subTitleStyle?: ToolBarV2TitleStyle
```

副标题文字样式。

**Type:** [ToolBarV2TitleStyle](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2titlestyle-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2TitleConfigs-subTitleStyle?: ToolBarV2TitleStyle--><!--Device-ToolBarV2TitleConfigs-subTitleStyle?: ToolBarV2TitleStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## visible

```TypeScript
visible?: boolean
```

标题是否可见。默认值: true。true表示标题可见，false表示标题不可见。

**Type:** boolean

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2TitleConfigs-visible?: boolean--><!--Device-ToolBarV2TitleConfigs-visible?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
