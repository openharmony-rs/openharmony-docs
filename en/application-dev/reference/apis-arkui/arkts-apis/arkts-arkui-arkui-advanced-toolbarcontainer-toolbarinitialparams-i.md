# ToolBarInitialParams

```TypeScript
export interface ToolBarInitialParams
```

工具栏初始位置参数，指定创建时的停靠区域、方向和状态。

**Since:** 26.1.0

<!--Device-unnamed-export interface ToolBarInitialParams--><!--Device-unnamed-export interface ToolBarInitialParams-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarState, DockArea, DockCornerMode, ToolBarSafeAreaMode, HandednessAdaptationMode, ToolBarFloatingOptions, ToolBarFloatingConfigs, ToolBarMinimizeOptions, ToolBarMinimizeConfigs, ToolBarController, ToolBarInitialParams, ToolBarParams, ToolBarConfigs, ToolBarCallbacks, ToolBarDockOffsetOptions, ToolBarSafeAreaOptions, ToolBarContainerOptions, ToolBarContainerConfigs, ToolBarContainer, ToolBarDragStateCallback, ToolBarDragOffsetCallback, ToolBarStateCallback, ToolBarDockCallback, } from '@kit.ArkUI';
```

## direction

```TypeScript
direction?: Axis
```

工具栏初始停靠方向。默认与吸附的边保持方向一致。

**Type:** [Axis](arkts-arkui-axis-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarInitialParams-direction?: Axis--><!--Device-ToolBarInitialParams-direction?: Axis-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dockArea

```TypeScript
dockArea: DockArea
```

工具栏初始停靠的区域。

**Type:** [DockArea](arkts-arkui-arkui-advanced-toolbarcontainer-dockarea-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarInitialParams-dockArea: DockArea--><!--Device-ToolBarInitialParams-dockArea: DockArea-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state?: ToolBarState
```

工具栏初始状态。默认值：[FLOATING](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarstate-e.md#floating)。

**Type:** [ToolBarState](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarstate-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarInitialParams-state?: ToolBarState--><!--Device-ToolBarInitialParams-state?: ToolBarState-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
