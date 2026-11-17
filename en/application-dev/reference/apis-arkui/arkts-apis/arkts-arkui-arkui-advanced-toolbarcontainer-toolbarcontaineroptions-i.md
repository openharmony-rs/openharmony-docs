# ToolBarContainerOptions

```TypeScript
export interface ToolBarContainerOptions
```

配置工具栏容器的布局、安全区避让和握姿适配的选项。

**Since:** 26.1.0

<!--Device-unnamed-export interface ToolBarContainerOptions--><!--Device-unnamed-export interface ToolBarContainerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarState, DockArea, DockCornerMode, ToolBarSafeAreaMode, HandednessAdaptationMode, ToolBarFloatingOptions, ToolBarFloatingConfigs, ToolBarMinimizeOptions, ToolBarMinimizeConfigs, ToolBarController, ToolBarInitialParams, ToolBarParams, ToolBarConfigs, ToolBarCallbacks, ToolBarDockOffsetOptions, ToolBarSafeAreaOptions, ToolBarContainerOptions, ToolBarContainerConfigs, ToolBarContainer, ToolBarDragStateCallback, ToolBarDragOffsetCallback, ToolBarStateCallback, ToolBarDockCallback, } from '@kit.ArkUI';
```

## adaptToHandedness

```TypeScript
adaptToHandedness?: HandednessAdaptationMode
```

接入智感握姿模式。默认值：HandednessAdaptationMode.NONE。仅在单工具栏时生效。

**Type:** [HandednessAdaptationMode](arkts-arkui-arkui-advanced-toolbarcontainer-handednessadaptationmode-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarContainerOptions-adaptToHandedness?: HandednessAdaptationMode--><!--Device-ToolBarContainerOptions-adaptToHandedness?: HandednessAdaptationMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dockOffset

```TypeScript
dockOffset?: ToolBarDockOffsetOptions
```

浮动工具栏的停靠偏移量。

**Type:** [ToolBarDockOffsetOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbardockoffsetoptions-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarContainerOptions-dockOffset?: ToolBarDockOffsetOptions--><!--Device-ToolBarContainerOptions-dockOffset?: ToolBarDockOffsetOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## gutter

```TypeScript
gutter?: LengthMetrics
```

工具栏超长溢出时的避让间隔。

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarContainerOptions-gutter?: LengthMetrics--><!--Device-ToolBarContainerOptions-gutter?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## safeArea

```TypeScript
safeArea?: ToolBarSafeAreaOptions
```

安全区避让模式。默认值：各边为[NONE](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarsafeareamode-e.md#none)。

**Type:** [ToolBarSafeAreaOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarsafeareaoptions-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarContainerOptions-safeArea?: ToolBarSafeAreaOptions--><!--Device-ToolBarContainerOptions-safeArea?: ToolBarSafeAreaOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
