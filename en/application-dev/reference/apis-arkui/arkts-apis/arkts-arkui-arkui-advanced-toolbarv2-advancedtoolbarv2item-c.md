# AdvancedToolbarV2Item

```TypeScript
export declare class AdvancedToolbarV2Item extends ToolBarV2Item
```

Defines the advanced toolbar item.

Extends [ToolBarV2Item](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2item-c.md) with advanced layout capabilities such as custom builder, title configuration, placement, display priority, activated background color, item size, separator, text visibility, overflow menu, and item grouping.

Items with the same non-empty `groupID` form a group. Group-level configuration (placement, spacing, container style) is read from the first item in the array that carries that `groupID`.

**Inheritance/Implementation:** AdvancedToolbarV2Item extends [ToolBarV2Item](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2item-c.md)

**Since:** 26.1.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class AdvancedToolbarV2Item extends ToolBarV2Item--><!--Device-unnamed-export declare class AdvancedToolbarV2Item extends ToolBarV2Item-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolbarV2Item, AdvancedToolbarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolbarV2ItemGroupStyle, ToolbarV2ItemGroupStyleOptions, ToolbarV2ItemPlacement, ToolbarV2OverflowMenuStyle, ToolbarV2PaddingOptions, ToolbarV2StyleConfigs, ToolbarV2StyleOptions, ToolbarV2TitleConfigs, ToolbarV2TitleOptions, ToolbarV2TitleStyle, ToolbarV2TitleStyleOptions } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: AdvancedToolbarV2ItemOptions)
```

The constructor used to create a AdvancedToolbarV2Item object.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2Item-constructor(options?: AdvancedToolbarV2ItemOptions)--><!--Device-AdvancedToolbarV2Item-constructor(options?: AdvancedToolbarV2ItemOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AdvancedToolbarV2ItemOptions](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2itemoptions-i.md) | No | item info. |

## activatedBackgroundColor

```TypeScript
activatedBackgroundColor?: ColorMetrics
```

Item background color in `ACTIVATE` status (activated background color). Only applies to icon-only items; icon+text items cannot set a background color. Defaults to transparent when not specified. Recommend using `$r('sys.color.comp_background_emphasize')` (HarmonyOS blue). Default value: Color.Transparent.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2Item-activatedBackgroundColor?: ColorMetrics--><!--Device-AdvancedToolbarV2Item-activatedBackgroundColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder?: CustomBuilder
```

Custom content builder for the toolbar item. When set, content and icon are ignored. Default value: undefined.

**Type:** [CustomBuilder](../arkts-components/arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2Item-builder?: CustomBuilder--><!--Device-AdvancedToolbarV2Item-builder?: CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayPriority

```TypeScript
displayPriority?: number
```

Display priority of the toolbar item in the layout container. Higher values indicate higher display priority. Value range: [0,10]. Default value: 1.

**Type:** number

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2Item-displayPriority?: number--><!--Device-AdvancedToolbarV2Item-displayPriority?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## groupID

```TypeScript
groupID?: string
```

Group identifier. Items sharing the same non-empty `groupID` are rendered as a visual group. Group-level configuration is read from the first item in the array that carries this `groupID`. Default value: undefined.

**Type:** string

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2Item-groupID?: string--><!--Device-AdvancedToolbarV2Item-groupID?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## groupStyle

```TypeScript
groupStyle?: ToolbarV2ItemGroupStyle
```

Style configuration for the group that this item belongs to. Only the value on the first item (in array order) carrying a given `groupID` takes effect; values on subsequent items with the same `groupID` are ignored. Default value: undefined.

**Type:** [ToolbarV2ItemGroupStyle](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemgroupstyle-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2Item-groupStyle?: ToolbarV2ItemGroupStyle--><!--Device-AdvancedToolbarV2Item-groupStyle?: ToolbarV2ItemGroupStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

Unique identifier for the toolbar item.

**Type:** string

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2Item-id?: string--><!--Device-AdvancedToolbarV2Item-id?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isShowOverflowMenu

```TypeScript
isShowOverflowMenu?: boolean
```

Whether to display the overflowMenu of the toolbar in this item. Default value: false.

**Type:** boolean

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2Item-isShowOverflowMenu?: boolean--><!--Device-AdvancedToolbarV2Item-isShowOverflowMenu?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isShowSeparator

```TypeScript
isShowSeparator?: boolean
```

Whether to show a separator after this item. When true, a separator is rendered after this item (not after the last item in the toolbar). Default value: false.

**Type:** boolean

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2Item-isShowSeparator?: boolean--><!--Device-AdvancedToolbarV2Item-isShowSeparator?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isShowText

```TypeScript
isShowText?: boolean
```

Whether to display the text content of the toolbar item. When set to false, the text specified by `content` is not rendered in the toolbar, but `content` is still used for overflow menu identification. This is useful when an icon-only item still needs text identification in the overflow menu. Default value: true.

**Type:** boolean

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2Item-isShowText?: boolean--><!--Device-AdvancedToolbarV2Item-isShowText?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSize

```TypeScript
itemSize?: Size
```

Item size (width × height) for the toolbar item. Default value: mainAxis 56vp x crossAxis 48vp. When horizontal: 56vp(width) x 48vp(height). When vertical: 48vp(width) x 56vp(height).

**Type:** Size

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2Item-itemSize?: Size--><!--Device-AdvancedToolbarV2Item-itemSize?: Size-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placement

```TypeScript
placement?: ToolbarV2ItemPlacement
```

Placement position of the toolbar item. Default value: ToolbarV2ItemPlacement.MAIN.

**Type:** [ToolbarV2ItemPlacement](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemplacement-e.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2Item-placement?: ToolbarV2ItemPlacement--><!--Device-AdvancedToolbarV2Item-placement?: ToolbarV2ItemPlacement-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## titleConfigs

```TypeScript
titleConfigs?: ToolbarV2TitleConfigs
```

Define advanced toolbarV2 title settings. When not provided, no title is rendered.

**Type:** [ToolbarV2TitleConfigs](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2titleconfigs-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolbarV2Item-titleConfigs?: ToolbarV2TitleConfigs--><!--Device-AdvancedToolbarV2Item-titleConfigs?: ToolbarV2TitleConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
