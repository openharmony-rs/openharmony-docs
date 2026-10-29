# ToolbarV2ItemGroupStyleOptions

```TypeScript
export interface ToolbarV2ItemGroupStyleOptions
```

Defines the constructor options for ToolbarV2ItemGroupStyle.

**Since:** 26.1.0

<!--Device-unnamed-export interface ToolbarV2ItemGroupStyleOptions--><!--Device-unnamed-export interface ToolbarV2ItemGroupStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolbarV2Item, AdvancedToolbarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolbarV2ItemGroupStyle, ToolbarV2ItemGroupStyleOptions, ToolbarV2ItemPlacement, ToolbarV2OverflowMenuStyle, ToolbarV2PaddingOptions, ToolbarV2StyleConfigs, ToolbarV2StyleOptions, ToolbarV2TitleConfigs, ToolbarV2TitleOptions, ToolbarV2TitleStyle, ToolbarV2TitleStyleOptions } from '@kit.ArkUI';
```

## backgroundColor

```TypeScript
backgroundColor?: ColorMetrics
```

Background color of the group container. Default value: $r('sys.color.comp_background_primary').

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2ItemGroupStyleOptions-backgroundColor?: ColorMetrics--><!--Device-ToolbarV2ItemGroupStyleOptions-backgroundColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ColorMetrics
```

Border color of the group container. Default value: undefined.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2ItemGroupStyleOptions-borderColor?: ColorMetrics--><!--Device-ToolbarV2ItemGroupStyleOptions-borderColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: LengthMetrics
```

Border radius of the group container. Default value: undefined.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2ItemGroupStyleOptions-borderRadius?: LengthMetrics--><!--Device-ToolbarV2ItemGroupStyleOptions-borderRadius?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: LengthMetrics
```

Border width of the group container. Default value: undefined.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2ItemGroupStyleOptions-borderWidth?: LengthMetrics--><!--Device-ToolbarV2ItemGroupStyleOptions-borderWidth?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## padding

```TypeScript
padding?: ToolbarV2PaddingOptions
```

Padding of the group container. Default value: undefined.

**Type:** [ToolbarV2PaddingOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2paddingoptions-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2ItemGroupStyleOptions-padding?: ToolbarV2PaddingOptions--><!--Device-ToolbarV2ItemGroupStyleOptions-padding?: ToolbarV2PaddingOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placement

```TypeScript
placement?: ToolbarV2ItemPlacement
```

Placement position of the group within the toolbar. The group placement takes precedence over the placement of individual items within the group. Default value: ToolbarV2ItemPlacement.MAIN.

**Type:** [ToolbarV2ItemPlacement](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemplacement-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2ItemGroupStyleOptions-placement?: ToolbarV2ItemPlacement--><!--Device-ToolbarV2ItemGroupStyleOptions-placement?: ToolbarV2ItemPlacement-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: LengthMetrics
```

Spacing between items within the group. Default value: 0vp.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2ItemGroupStyleOptions-space?: LengthMetrics--><!--Device-ToolbarV2ItemGroupStyleOptions-space?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stateEffect

```TypeScript
stateEffect?: boolean
```

Whether to show the press-state effect for items within the group. Default value: true.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2ItemGroupStyleOptions-stateEffect?: boolean--><!--Device-ToolbarV2ItemGroupStyleOptions-stateEffect?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
