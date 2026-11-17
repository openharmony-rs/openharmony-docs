# AdvancedToolBarV2ItemParams

```TypeScript
export interface AdvancedToolBarV2ItemParams extends ToolBarV2ItemOptions
```

声明AdvancedToolBarV2Item的选项。

使用高级字段扩展[ToolBarV2ItemOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemoptions-i.md)。内容是作为必填字段继承；在项上使用isShowText来控制文本是否被渲染。

**Inheritance/Implementation:** AdvancedToolBarV2ItemParams extends [ToolBarV2ItemOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemoptions-i.md)

**Since:** 26.1.0

<!--Device-unnamed-export interface AdvancedToolBarV2ItemParams extends ToolBarV2ItemOptions--><!--Device-unnamed-export interface AdvancedToolBarV2ItemParams extends ToolBarV2ItemOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolBarV2Item, AdvancedToolBarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolBarV2ItemGroupStyle, ToolBarV2ItemGroupStyleOptions, ToolBarV2ItemPlacement, ToolBarV2OverflowMenuStyle, ToolBarV2PaddingOptions, ToolBarV2StyleConfigs, ToolBarV2StyleOptions, ToolBarV2TitleConfigs, ToolBarV2TitleOptions, ToolBarV2TitleStyle, ToolBarV2TitleStyleOptions, ToolBarV2MaterialStyle } from '@kit.ArkUI';
```

## activatedBackgroundColor

```TypeScript
activatedBackgroundColor?: ColorMetrics
```

处于ACTIVATE状态的项目背景色（激活的背景色）。仅适用于仅有图标的项目，图标+文本项目不能设置背景颜色。建议使用$r('sys.color.comp_background_emphasize')。默认值：undefined，表示无颜色。

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2ItemParams-activatedBackgroundColor?: ColorMetrics--><!--Device-AdvancedToolBarV2ItemParams-activatedBackgroundColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder?: CustomBuilder
```

工具栏项的自定义内容生成器。设置时，内容和图标将被忽略。

**Type:** [CustomBuilder](../arkts-components/arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2ItemParams-builder?: CustomBuilder--><!--Device-AdvancedToolBarV2ItemParams-builder?: CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayPriority

```TypeScript
displayPriority?: number
```

布局容器中工具栏项的显示优先级。值越高，显示优先级越高。取值范围[0, 10]。默认值：1。

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2ItemParams-displayPriority?: number--><!--Device-AdvancedToolBarV2ItemParams-displayPriority?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## groupID

```TypeScript
groupID?: string
```

组标识。相同非空groupID的项作为一个视觉群体。同一groupID的第一个项决定组的位置。默认值：undefined，表示没有groupID。

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2ItemParams-groupID?: string--><!--Device-AdvancedToolBarV2ItemParams-groupID?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## groupStyle

```TypeScript
groupStyle?: ToolBarV2ItemGroupStyle
```

此项目所属组的样式配置。相同groupID下第一个设置了groupStyle的样式配置生效；具有相同groupID的后续项上的值将被忽略。

**Type:** [ToolBarV2ItemGroupStyle](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemgroupstyle-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2ItemParams-groupStyle?: ToolBarV2ItemGroupStyle--><!--Device-AdvancedToolBarV2ItemParams-groupStyle?: ToolBarV2ItemGroupStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

工具栏项的唯一标识符。默认值：undefined，表示未设置id。

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2ItemParams-id?: string--><!--Device-AdvancedToolBarV2ItemParams-id?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isShowOverflowMenu

```TypeScript
isShowOverflowMenu?: boolean
```

此项中是否显示为工具栏的溢出菜单。默认值：undefined。值为undefined或不设置时默认为false。

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2ItemParams-isShowOverflowMenu?: boolean--><!--Device-AdvancedToolBarV2ItemParams-isShowOverflowMenu?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isShowSeparator

```TypeScript
isShowSeparator?: boolean
```

是否在该项后显示分隔符。如果为true，则在该项之后呈现分隔符（而不是在工具栏中的最后一项之后）。默认值：false，表示不显示分隔符。

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2ItemParams-isShowSeparator?: boolean--><!--Device-AdvancedToolBarV2ItemParams-isShowSeparator?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isShowText

```TypeScript
isShowText?: boolean
```

是否显示工具栏项的文本内容。当设置为false时，由content指定的文本不会在工具栏中呈现。针对项中仅需图标显示的场景使用。默认值：undefined。值为undefined或不设置时默认为true，表示同时存在图标和文本时文本可显示。

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2ItemParams-isShowText?: boolean--><!--Device-AdvancedToolBarV2ItemParams-isShowText?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSize

```TypeScript
itemSize?: Size
```

工具栏项的项大小（宽×高）。

**Type:** Size

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2ItemParams-itemSize?: Size--><!--Device-AdvancedToolBarV2ItemParams-itemSize?: Size-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placement

```TypeScript
placement?: ToolBarV2ItemPlacement
```

工具栏项的放置位置。默认值：ToolBarV2ItemPlacement.MAIN。

**Type:** [ToolBarV2ItemPlacement](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemplacement-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2ItemParams-placement?: ToolBarV2ItemPlacement--><!--Device-AdvancedToolBarV2ItemParams-placement?: ToolBarV2ItemPlacement-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## titleConfigs

```TypeScript
titleConfigs?: ToolBarV2TitleConfigs
```

定义高级工具栏V2标题设置。如果不提供，则不显示标题。

**Type:** [ToolBarV2TitleConfigs](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2titleconfigs-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2ItemParams-titleConfigs?: ToolBarV2TitleConfigs--><!--Device-AdvancedToolBarV2ItemParams-titleConfigs?: ToolBarV2TitleConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
