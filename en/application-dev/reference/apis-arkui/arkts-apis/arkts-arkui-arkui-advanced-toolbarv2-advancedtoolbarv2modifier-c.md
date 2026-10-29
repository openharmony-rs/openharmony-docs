# AdvancedToolBarV2Modifier

```TypeScript
export declare class AdvancedToolBarV2Modifier
```

Advanced modifier for ToolBarV2. Merges layout attributes, style configs, and overflow menu style into a single modifier class.

Uses chainable setter methods that accept original config objects.

**Since:** 26.1.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class AdvancedToolBarV2Modifier--><!--Device-unnamed-export declare class AdvancedToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolbarV2Item, AdvancedToolbarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolbarV2ItemGroupStyle, ToolbarV2ItemGroupStyleOptions, ToolbarV2ItemPlacement, ToolbarV2OverflowMenuStyle, ToolbarV2PaddingOptions, ToolbarV2StyleConfigs, ToolbarV2StyleOptions, ToolbarV2TitleConfigs, ToolbarV2TitleOptions, ToolbarV2TitleStyle, ToolbarV2TitleStyleOptions } from '@kit.ArkUI';
```

## crossAxisLength

```TypeScript
crossAxisLength(value: LengthMetrics): AdvancedToolBarV2Modifier
```

Sets the breadth of the toolbar perpendicular to the layout direction.

Horizontal: controls height. Vertical: controls width. When not set, the cross-axis is auto-sized by content.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Modifier-crossAxisLength(value: LengthMetrics): AdvancedToolBarV2Modifier--><!--Device-AdvancedToolBarV2Modifier-crossAxisLength(value: LengthMetrics): AdvancedToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Yes | The breadth value perpendicular to the layout direction. |

**Return value:**

| Type | Description |
| --- | --- |
| [AdvancedToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2modifier-c.md) | Returns this modifier for chaining. |

## direction

```TypeScript
direction(value: Axis): AdvancedToolBarV2Modifier
```

Sets the layout direction of the toolbar.

HORIZONTAL: items arranged in a row (default). VERTICAL: items arranged in a column.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Modifier-direction(value: Axis): AdvancedToolBarV2Modifier--><!--Device-AdvancedToolBarV2Modifier-direction(value: Axis): AdvancedToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Axis](arkts-arkui-axis-e.md) | Yes | The direction value. |

**Return value:**

| Type | Description |
| --- | --- |
| [AdvancedToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2modifier-c.md) | Returns this modifier for chaining. |

## mainAxisLength

```TypeScript
mainAxisLength(value: LengthMetrics): AdvancedToolBarV2Modifier
```

Sets the length of the toolbar along the layout direction.

Horizontal: controls width. Vertical: controls height. Default value: '100%'.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Modifier-mainAxisLength(value: LengthMetrics): AdvancedToolBarV2Modifier--><!--Device-AdvancedToolBarV2Modifier-mainAxisLength(value: LengthMetrics): AdvancedToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Yes | The length value along the layout direction. |

**Return value:**

| Type | Description |
| --- | --- |
| [AdvancedToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2modifier-c.md) | Returns this modifier for chaining. |

## overflowMenuStyle

```TypeScript
overflowMenuStyle(menuStyle: ToolbarV2OverflowMenuStyle): AdvancedToolBarV2Modifier
```

Sets the style configuration for the overflow menu popup.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Modifier-overflowMenuStyle(menuStyle: ToolbarV2OverflowMenuStyle): AdvancedToolBarV2Modifier--><!--Device-AdvancedToolBarV2Modifier-overflowMenuStyle(menuStyle: ToolbarV2OverflowMenuStyle): AdvancedToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| menuStyle | [ToolbarV2OverflowMenuStyle](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2overflowmenustyle-i.md) | Yes | The overflow menu style configuration object. |

**Return value:**

| Type | Description |
| --- | --- |
| [AdvancedToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2modifier-c.md) | Returns this modifier for chaining. |

## style

```TypeScript
style(styleConfigs: ToolbarV2StyleConfigs): AdvancedToolBarV2Modifier
```

Sets the toolbar style configuration.

Controls background, padding, groupSpace, border, and item active/disabled colors.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Modifier-style(styleConfigs: ToolbarV2StyleConfigs): AdvancedToolBarV2Modifier--><!--Device-AdvancedToolBarV2Modifier-style(styleConfigs: ToolbarV2StyleConfigs): AdvancedToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| styleConfigs | [ToolbarV2StyleConfigs](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2styleconfigs-c.md) | Yes | The style configuration object. |

**Return value:**

| Type | Description |
| --- | --- |
| [AdvancedToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2modifier-c.md) | Returns this modifier for chaining. |
