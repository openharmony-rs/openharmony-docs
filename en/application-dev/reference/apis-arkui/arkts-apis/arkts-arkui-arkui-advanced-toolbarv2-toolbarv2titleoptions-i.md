# ToolbarV2TitleOptions

```TypeScript
export interface ToolbarV2TitleOptions
```

Defines the constructor options for ToolbarV2TitleConfigs.

**Since:** 26.1.0

<!--Device-unnamed-export interface ToolbarV2TitleOptions--><!--Device-unnamed-export interface ToolbarV2TitleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolbarV2Item, AdvancedToolbarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolbarV2ItemGroupStyle, ToolbarV2ItemGroupStyleOptions, ToolbarV2ItemPlacement, ToolbarV2OverflowMenuStyle, ToolbarV2PaddingOptions, ToolbarV2StyleConfigs, ToolbarV2StyleOptions, ToolbarV2TitleConfigs, ToolbarV2TitleOptions, ToolbarV2TitleStyle, ToolbarV2TitleStyleOptions } from '@kit.ArkUI';
```

## content

```TypeScript
content?: ResourceStr
```

Title text content. Required when constructing ToolbarV2TitleConfigs. Default value: undefined.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2TitleOptions-content?: ResourceStr--><!--Device-ToolbarV2TitleOptions-content?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placement

```TypeScript
placement?: ToolbarV2ItemPlacement
```

Placement position of the title within the toolbar. Reuses `ToolbarV2ItemPlacement` — the title is arranged in the same area as items with the same placement. Default value: ToolbarV2ItemPlacement.LEADING.

**Type:** [ToolbarV2ItemPlacement](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemplacement-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2TitleOptions-placement?: ToolbarV2ItemPlacement--><!--Device-ToolbarV2TitleOptions-placement?: ToolbarV2ItemPlacement-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: ToolbarV2TitleStyle
```

Title text style.

**Type:** [ToolbarV2TitleStyle](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2titlestyle-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2TitleOptions-style?: ToolbarV2TitleStyle--><!--Device-ToolbarV2TitleOptions-style?: ToolbarV2TitleStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## visible

```TypeScript
visible?: boolean
```

Whether the title is visible. Default value: true.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2TitleOptions-visible?: boolean--><!--Device-ToolbarV2TitleOptions-visible?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
