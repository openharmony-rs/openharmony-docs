# ToolBarMinimizeConfigs

```TypeScript
export class ToolBarMinimizeConfigs
```

最小化悬浮球的可观察配置存储，与[ToolBarMinimizeOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarminimizeoptions-i.md)对应。

**Since:** 26.1.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export class ToolBarMinimizeConfigs--><!--Device-unnamed-export class ToolBarMinimizeConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarState, DockArea, DockCornerMode, ToolBarSafeAreaMode, HandednessAdaptationMode, ToolBarFloatingOptions, ToolBarFloatingConfigs, ToolBarMinimizeOptions, ToolBarMinimizeConfigs, ToolBarController, ToolBarInitialParams, ToolBarParams, ToolBarConfigs, ToolBarCallbacks, ToolBarDockOffsetOptions, ToolBarSafeAreaOptions, ToolBarContainerOptions, ToolBarContainerConfigs, ToolBarContainer, ToolBarDragStateCallback, ToolBarDragOffsetCallback, ToolBarStateCallback, ToolBarDockCallback, } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ToolBarMinimizeOptions)
```

ToolBarMinimizeConfigs的构造函数。当options省略时，所有字段使用各自的默认值。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarMinimizeConfigs-constructor(options?: ToolBarMinimizeOptions)--><!--Device-ToolBarMinimizeConfigs-constructor(options?: ToolBarMinimizeOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ToolBarMinimizeOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarminimizeoptions-i.md) | No | 最小化悬浮球选项。 |

## builder

```TypeScript
builder?: CustomBuilder
```

自定义构建器。默认值为undefined，无自定义内容。

**Type:** [CustomBuilder](../arkts-components/arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarMinimizeConfigs-builder?: CustomBuilder--><!--Device-ToolBarMinimizeConfigs-builder?: CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buoySize

```TypeScript
buoySize?: LengthMetrics
```

最小化悬浮球的直径。

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarMinimizeConfigs-buoySize?: LengthMetrics--><!--Device-ToolBarMinimizeConfigs-buoySize?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr | SymbolGlyphModifier
```

图标。默认值为undefined，表示无图标内容。

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md) &#124; [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarMinimizeConfigs-icon?: ResourceStr | SymbolGlyphModifier--><!--Device-ToolBarMinimizeConfigs-icon?: ResourceStr | SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconColor

```TypeScript
iconColor?: ColorMetrics
```

图标颜色。默认值为$r('sys.color.icon_primary')。

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarMinimizeConfigs-iconColor?: ColorMetrics--><!--Device-ToolBarMinimizeConfigs-iconColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconSize

```TypeScript
iconSize?: LengthMetrics
```

图标尺寸。

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarMinimizeConfigs-iconSize?: LengthMetrics--><!--Device-ToolBarMinimizeConfigs-iconSize?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr
```

文本标签。默认值为undefined，表示无文本内容。

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarMinimizeConfigs-text?: ResourceStr--><!--Device-ToolBarMinimizeConfigs-text?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textColor

```TypeScript
textColor?: ColorMetrics
```

文本颜色。默认值为$r('sys.color.font_primary')。

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarMinimizeConfigs-textColor?: ColorMetrics--><!--Device-ToolBarMinimizeConfigs-textColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
