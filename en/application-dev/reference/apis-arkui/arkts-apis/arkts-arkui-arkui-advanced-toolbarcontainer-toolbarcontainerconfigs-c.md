# ToolBarContainerConfigs

```TypeScript
export class ToolBarContainerConfigs
```

工具栏容器的可观察配置存储，与[ToolBarContainerOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarcontaineroptions-i.md)对应。

**Since:** 26.1.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export class ToolBarContainerConfigs--><!--Device-unnamed-export class ToolBarContainerConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarState, DockArea, DockCornerMode, ToolBarSafeAreaMode, HandednessAdaptationMode, ToolBarFloatingOptions, ToolBarFloatingConfigs, ToolBarMinimizeOptions, ToolBarMinimizeConfigs, ToolBarController, ToolBarInitialParams, ToolBarParams, ToolBarConfigs, ToolBarCallbacks, ToolBarDockOffsetOptions, ToolBarSafeAreaOptions, ToolBarContainerOptions, ToolBarContainerConfigs, ToolBarContainer, ToolBarDragStateCallback, ToolBarDragOffsetCallback, ToolBarStateCallback, ToolBarDockCallback, } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ToolBarContainerOptions)
```

构造函数。当options省略时，所有字段使用各自的默认值。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarContainerConfigs-constructor(options?: ToolBarContainerOptions)--><!--Device-ToolBarContainerConfigs-constructor(options?: ToolBarContainerOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ToolBarContainerOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarcontaineroptions-i.md) | No | 容器选项。 |

## adaptToHandedness

```TypeScript
adaptToHandedness?: HandednessAdaptationMode
```

接入智感握姿模式。默认值：HandednessAdaptationMode.NONE。

**Type:** [HandednessAdaptationMode](arkts-arkui-arkui-advanced-toolbarcontainer-handednessadaptationmode-e.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarContainerConfigs-adaptToHandedness?: HandednessAdaptationMode--><!--Device-ToolBarContainerConfigs-adaptToHandedness?: HandednessAdaptationMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dockOffset

```TypeScript
dockOffset?: ToolBarDockOffsetOptions
```

停靠偏移量，单位为vp。默认值：各边为16vp。

**Type:** [ToolBarDockOffsetOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbardockoffsetoptions-i.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarContainerConfigs-dockOffset?: ToolBarDockOffsetOptions--><!--Device-ToolBarContainerConfigs-dockOffset?: ToolBarDockOffsetOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## gutter

```TypeScript
gutter?: LengthMetrics
```

工具栏之间的间隔。

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarContainerConfigs-gutter?: LengthMetrics--><!--Device-ToolBarContainerConfigs-gutter?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## safeArea

```TypeScript
safeArea?: ToolBarSafeAreaOptions
```

安全区模式。默认值：各边为ToolBarSafeAreaMode.NONE。

**Type:** [ToolBarSafeAreaOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarsafeareaoptions-i.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarContainerConfigs-safeArea?: ToolBarSafeAreaOptions--><!--Device-ToolBarContainerConfigs-safeArea?: ToolBarSafeAreaOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
