# AdvancedToolBarV2Modifier

```TypeScript
export declare class AdvancedToolBarV2Modifier
```

ToolBarV2的高级修饰符。合并布局属性、样式配置、和溢出菜单样式到单个修饰符类中。

使用可链接的setter方法，这些方法接受原始配置对象。

**Since:** 26.1.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class AdvancedToolBarV2Modifier--><!--Device-unnamed-export declare class AdvancedToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolBarV2Item, AdvancedToolBarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolBarV2ItemGroupStyle, ToolBarV2ItemGroupStyleOptions, ToolBarV2ItemPlacement, ToolBarV2OverflowMenuStyle, ToolBarV2PaddingOptions, ToolBarV2StyleConfigs, ToolBarV2StyleOptions, ToolBarV2TitleConfigs, ToolBarV2TitleOptions, ToolBarV2TitleStyle, ToolBarV2TitleStyleOptions, ToolBarV2MaterialStyle } from '@kit.ArkUI';
```

## crossAxisLength

```TypeScript
crossAxisLength(value: LengthMetrics): AdvancedToolBarV2Modifier
```

设置工具栏垂直于布局方向的宽度。

水平：控制高度。垂直：控制宽度。默认值：undefined。值为undefined或未设置时，值为56vp。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Modifier-crossAxisLength(value: LengthMetrics): AdvancedToolBarV2Modifier--><!--Device-AdvancedToolBarV2Modifier-crossAxisLength(value: LengthMetrics): AdvancedToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Yes | 垂直于布局方向的宽度值。 |

**Return value:**

| Type | Description |
| --- | --- |
| [AdvancedToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2modifier-c.md) | 返回用于链接的此修饰符。 |

## direction

```TypeScript
direction(value: Axis): AdvancedToolBarV2Modifier
```

设置工具栏的布局方向。

默认值：undefined。值为undefined或未设置时，水平排列。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Modifier-direction(value: Axis): AdvancedToolBarV2Modifier--><!--Device-AdvancedToolBarV2Modifier-direction(value: Axis): AdvancedToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Axis](arkts-arkui-axis-e.md) | Yes | 方向值。 |

**Return value:**

| Type | Description |
| --- | --- |
| [AdvancedToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2modifier-c.md) | 返回用于链接的此修饰符。 |

## mainAxisLength

```TypeScript
mainAxisLength(value: LengthMetrics): AdvancedToolBarV2Modifier
```

设置工具栏沿布局方向的长度。

水平：控制宽度。垂直：控制高度。默认值：undefined。值为undefined或不设置时，默认占满。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Modifier-mainAxisLength(value: LengthMetrics): AdvancedToolBarV2Modifier--><!--Device-AdvancedToolBarV2Modifier-mainAxisLength(value: LengthMetrics): AdvancedToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Yes | 沿布局方向的长度值。 |

**Return value:**

| Type | Description |
| --- | --- |
| [AdvancedToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2modifier-c.md) | 返回用于链接的此修饰符。 |

## overflowMenuStyle

```TypeScript
overflowMenuStyle(menuStyle: ToolBarV2OverflowMenuStyle): AdvancedToolBarV2Modifier
```

设置溢出菜单弹出窗口的样式配置。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Modifier-overflowMenuStyle(menuStyle: ToolBarV2OverflowMenuStyle): AdvancedToolBarV2Modifier--><!--Device-AdvancedToolBarV2Modifier-overflowMenuStyle(menuStyle: ToolBarV2OverflowMenuStyle): AdvancedToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| menuStyle | [ToolBarV2OverflowMenuStyle](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2overflowmenustyle-i.md) | Yes | 溢出菜单样式配置对象。 |

**Return value:**

| Type | Description |
| --- | --- |
| [AdvancedToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2modifier-c.md) | 返回用于链接的此修饰符。 |

## style

```TypeScript
style(styleConfigs: ToolBarV2StyleConfigs): AdvancedToolBarV2Modifier
```

设置工具栏样式配置。

控制背景、填充、groupSpace、边框和项目活动/禁用的颜色。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-AdvancedToolBarV2Modifier-style(styleConfigs: ToolBarV2StyleConfigs): AdvancedToolBarV2Modifier--><!--Device-AdvancedToolBarV2Modifier-style(styleConfigs: ToolBarV2StyleConfigs): AdvancedToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| styleConfigs | [ToolBarV2StyleConfigs](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2styleconfigs-c.md) | Yes | 样式配置对象。 |

**Return value:**

| Type | Description |
| --- | --- |
| [AdvancedToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2modifier-c.md) | 返回用于链接的此修饰符。 |
