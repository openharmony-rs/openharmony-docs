# AdvancedToolbarV2ItemOptions

```TypeScript
export interface AdvancedToolbarV2ItemOptions extends ToolBarV2ItemOptions
```

Declare the options of AdvancedToolbarV2Item.

Extends [ToolBarV2ItemOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemoptions-i.md) with advanced fields. `content` is inherited as a required field; use `isShowText` on the item to control whether the text is rendered.

**Inheritance/Implementation:** AdvancedToolbarV2ItemOptions extends [ToolBarV2ItemOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemoptions-i.md)

**Since:** 26.1.0

<!--Device-unnamed-export interface AdvancedToolbarV2ItemOptions extends ToolBarV2ItemOptions--><!--Device-unnamed-export interface AdvancedToolbarV2ItemOptions extends ToolBarV2ItemOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolbarV2Item, AdvancedToolbarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolbarV2ItemGroupStyle, ToolbarV2ItemGroupStyleOptions, ToolbarV2ItemPlacement, ToolbarV2OverflowMenuStyle, ToolbarV2PaddingOptions, ToolbarV2StyleConfigs, ToolbarV2StyleOptions, ToolbarV2TitleConfigs, ToolbarV2TitleOptions, ToolbarV2TitleStyle, ToolbarV2TitleStyleOptions } from '@kit.ArkUI';
```

## activatedBackgroundColor

```TypeScript
activatedBackgroundColor?: ColorMetrics
```

Item background color in `ACTIVATE` status (activated background color). Only applies to icon-only items; icon+text items cannot set a background color. Defaults to transparent when not specified. Recommend using `$r('sys.color.comp_background_emphasize')`. Default value: Color.Transparent.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2ItemOptions-activatedBackgroundColor?: ColorMetrics--><!--Device-AdvancedToolbarV2ItemOptions-activatedBackgroundColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder?: CustomBuilder
```

Custom content builder for the toolbar item. When set, content and icon are ignored. Default value: undefined.

**Type:** [CustomBuilder](../arkts-components/arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2ItemOptions-builder?: CustomBuilder--><!--Device-AdvancedToolbarV2ItemOptions-builder?: CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayPriority

```TypeScript
displayPriority?: number
```

Display priority of the toolbar item in the layout container. Higher values indicate higher display priority. The value range is [0, 10]. Default value: 1.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2ItemOptions-displayPriority?: number--><!--Device-AdvancedToolbarV2ItemOptions-displayPriority?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## groupID

```TypeScript
groupID?: string
```

Group identifier. Items sharing the same non-empty `groupID` are rendered as a visual group. Default value: undefined.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2ItemOptions-groupID?: string--><!--Device-AdvancedToolbarV2ItemOptions-groupID?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## groupStyle

```TypeScript
groupStyle?: ToolbarV2ItemGroupStyle
```

Style configuration for the group that this item belongs to. Only the value on the first item (in array order) carrying a given `groupID` takes effect; values on subsequent items with the same `groupID` are ignored. Default value: undefined.

**Type:** [ToolbarV2ItemGroupStyle](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemgroupstyle-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2ItemOptions-groupStyle?: ToolbarV2ItemGroupStyle--><!--Device-AdvancedToolbarV2ItemOptions-groupStyle?: ToolbarV2ItemGroupStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

Unique identifier for the toolbar item. Default value: undefined.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2ItemOptions-id?: string--><!--Device-AdvancedToolbarV2ItemOptions-id?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isShowOverflowMenu

```TypeScript
isShowOverflowMenu?: boolean
```

Whether to display the overflowMenu of the toolbar in this item. Default value: false.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2ItemOptions-isShowOverflowMenu?: boolean--><!--Device-AdvancedToolbarV2ItemOptions-isShowOverflowMenu?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isShowSeparator

```TypeScript
isShowSeparator?: boolean
```

Whether to show a separator after this item. When true, a separator is rendered after this item (not after the last item in the toolbar). Default value: false.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2ItemOptions-isShowSeparator?: boolean--><!--Device-AdvancedToolbarV2ItemOptions-isShowSeparator?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isShowText

```TypeScript
isShowText?: boolean
```

Whether to display the text content of the toolbar item. When set to false, the text specified by `content` is not rendered in the toolbar, but `content` is still used for accessibility and overflow menu identification. This is useful when an icon-only item still needs text identification in the overflow menu. Default value: true.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2ItemOptions-isShowText?: boolean--><!--Device-AdvancedToolbarV2ItemOptions-isShowText?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSize

```TypeScript
itemSize?: Size
```

Item size (width × height) for the toolbar item. Default value: mainAxis 56vp x crossAxis 48vp. When horizontal: 56vp(width) x 48vp(height). When vertical: 48vp(width) x 56vp(height).

**Type:** Size

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2ItemOptions-itemSize?: Size--><!--Device-AdvancedToolbarV2ItemOptions-itemSize?: Size-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placement

```TypeScript
placement?: ToolbarV2ItemPlacement
```

Placement position of the toolbar item. Default value: ToolbarV2ItemPlacement.MAIN.

**Type:** [ToolbarV2ItemPlacement](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemplacement-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2ItemOptions-placement?: ToolbarV2ItemPlacement--><!--Device-AdvancedToolbarV2ItemOptions-placement?: ToolbarV2ItemPlacement-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## titleConfigs

```TypeScript
titleConfigs?: ToolbarV2TitleConfigs
```

Define advanced toolbarV2 title settings. When not provided, no title is rendered.

**Type:** [ToolbarV2TitleConfigs](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2titleconfigs-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2ItemOptions-titleConfigs?: ToolbarV2TitleConfigs--><!--Device-AdvancedToolbarV2ItemOptions-titleConfigs?: ToolbarV2TitleConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
