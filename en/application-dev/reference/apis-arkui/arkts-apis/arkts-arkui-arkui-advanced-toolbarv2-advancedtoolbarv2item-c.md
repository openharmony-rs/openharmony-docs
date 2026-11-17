# AdvancedToolBarV2Item

```TypeScript
export declare class AdvancedToolBarV2Item extends ToolBarV2Item
```

定义高级工具栏项。

扩展[ToolBarV2Item](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2item-c.md)以高级布局功能，例如自定义生成器、标题配置、位置、显示优先级、激活的背景色、项目大小、分隔符、文本可见性、溢出菜单和项目分组。

> **说明：** 
> 具有相同非空groupID的项组成一个组，组级
> 配置（位置、间距、容器样式）从
> 数组中包含groupID的第一项。

**Inheritance/Implementation:** AdvancedToolBarV2Item extends [ToolBarV2Item](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2item-c.md)

**Since:** 26.1.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class AdvancedToolBarV2Item extends ToolBarV2Item--><!--Device-unnamed-export declare class AdvancedToolBarV2Item extends ToolBarV2Item-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolBarV2Item, AdvancedToolBarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolBarV2ItemGroupStyle, ToolBarV2ItemGroupStyleOptions, ToolBarV2ItemPlacement, ToolBarV2OverflowMenuStyle, ToolBarV2PaddingOptions, ToolBarV2StyleConfigs, ToolBarV2StyleOptions, ToolBarV2TitleConfigs, ToolBarV2TitleOptions, ToolBarV2TitleStyle, ToolBarV2TitleStyleOptions, ToolBarV2MaterialStyle } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(params: AdvancedToolBarV2ItemParams)
```

用于创建AdvancedToolBarV2Item对象的构造函数。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Item-constructor(params: AdvancedToolBarV2ItemParams)--><!--Device-AdvancedToolBarV2Item-constructor(params: AdvancedToolBarV2ItemParams)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [AdvancedToolBarV2ItemParams](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2itemparams-i.md) | Yes | 构造参数信息。 |

## activatedBackgroundColor

```TypeScript
activatedBackgroundColor?: ColorMetrics
```

处于ACTIVATE状态的项目背景色（激活的背景色）。仅适用于仅有图标的项目，图标+文本项目不能设置背景颜色。默认值：undefined。未设置时无颜色。建议使用$r（'sys.color.comp_background_emphasize'）（鸿蒙蓝色）。

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Item-activatedBackgroundColor?: ColorMetrics--><!--Device-AdvancedToolBarV2Item-activatedBackgroundColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder?: CustomBuilder
```

工具栏项的自定义内容生成器。默认值：undefined。设置时，内容和图标将被忽略。

**Type:** [CustomBuilder](../arkts-components/arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Item-builder?: CustomBuilder--><!--Device-AdvancedToolBarV2Item-builder?: CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayPriority

```TypeScript
displayPriority?: number
```

布局容器中工具栏项的显示优先级。值越高，显示优先级越高。默认值：1。取值范围：[0, 10]。

**Type:** number

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Item-displayPriority?: number--><!--Device-AdvancedToolBarV2Item-displayPriority?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## groupID

```TypeScript
groupID?: string
```

组标识。相同非空groupID的项作为一个视觉群体。同一groupID的第一个项决定组的位置。默认值：undefined。

**Type:** string

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Item-groupID?: string--><!--Device-AdvancedToolBarV2Item-groupID?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## groupStyle

```TypeScript
groupStyle?: ToolBarV2ItemGroupStyle
```

此项目所属组的样式配置。相同groupID下第一个设置了groupStyle的样式配置生效；具有相同groupID的后续项上的值将被忽略。默认值：undefined。

**Type:** [ToolBarV2ItemGroupStyle](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemgroupstyle-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Item-groupStyle?: ToolBarV2ItemGroupStyle--><!--Device-AdvancedToolBarV2Item-groupStyle?: ToolBarV2ItemGroupStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

工具栏项的唯一标识符。

**Type:** string

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Item-id?: string--><!--Device-AdvancedToolBarV2Item-id?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isShowOverflowMenu

```TypeScript
isShowOverflowMenu?: boolean
```

此项中是否显示为工具栏的溢出菜单。默认值：undefined。不设置时默认为false。

**Type:** boolean

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Item-isShowOverflowMenu?: boolean--><!--Device-AdvancedToolBarV2Item-isShowOverflowMenu?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isShowSeparator

```TypeScript
isShowSeparator?: boolean
```

是否在该项后显示分隔符。如果为true，则在该项之后呈现分隔符（而不是在工具栏中的最后一项之后）。默认值：undefined。不设置时，默认为false，不显示分隔符。

**Type:** boolean

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Item-isShowSeparator?: boolean--><!--Device-AdvancedToolBarV2Item-isShowSeparator?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isShowText

```TypeScript
isShowText?: boolean
```

是否显示工具栏项的文本内容。当设置为false时，由content指定的文本不会在工具栏中呈现。针对项中仅需图标显示的场景使用。默认值：undefined。

**Type:** boolean

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Item-isShowText?: boolean--><!--Device-AdvancedToolBarV2Item-isShowText?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSize

```TypeScript
itemSize?: Size
```

工具栏项的项大小（宽×高）。

**Type:** Size

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Item-itemSize?: Size--><!--Device-AdvancedToolBarV2Item-itemSize?: Size-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placement

```TypeScript
placement?: ToolBarV2ItemPlacement
```

工具栏项的放置位置。默认值：ToolBarV2ItemPlacement.MAIN。

**Type:** [ToolBarV2ItemPlacement](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemplacement-e.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Item-placement?: ToolBarV2ItemPlacement--><!--Device-AdvancedToolBarV2Item-placement?: ToolBarV2ItemPlacement-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## titleConfigs

```TypeScript
titleConfigs?: ToolBarV2TitleConfigs
```

定义高级工具栏V2标题设置。如果不提供，则不显示标题。

**Type:** [ToolBarV2TitleConfigs](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2titleconfigs-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Item-titleConfigs?: ToolBarV2TitleConfigs--><!--Device-AdvancedToolBarV2Item-titleConfigs?: ToolBarV2TitleConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
