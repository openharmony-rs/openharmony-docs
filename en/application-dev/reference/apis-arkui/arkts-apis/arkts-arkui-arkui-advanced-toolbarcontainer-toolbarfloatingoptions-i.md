# ToolBarFloatingOptions

```TypeScript
export interface ToolBarFloatingOptions
```

配置工具栏浮动行为的选项。

**Since:** 26.1.0

<!--Device-unnamed-export interface ToolBarFloatingOptions--><!--Device-unnamed-export interface ToolBarFloatingOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarState, DockArea, DockCornerMode, ToolBarSafeAreaMode, HandednessAdaptationMode, ToolBarFloatingOptions, ToolBarFloatingConfigs, ToolBarMinimizeOptions, ToolBarMinimizeConfigs, ToolBarController, ToolBarInitialParams, ToolBarParams, ToolBarConfigs, ToolBarCallbacks, ToolBarDockOffsetOptions, ToolBarSafeAreaOptions, ToolBarContainerOptions, ToolBarContainerConfigs, ToolBarContainer, ToolBarDragStateCallback, ToolBarDragOffsetCallback, ToolBarStateCallback, ToolBarDockCallback, } from '@kit.ArkUI';
```

## cornerMode

```TypeScript
cornerMode?: DockCornerMode
```

角落吸附模式。MINIMIZE（默认）表示吸附到角落并跟随所在边缘；EXPAND表示保持拖拽方向。

**Type:** [DockCornerMode](arkts-arkui-arkui-advanced-toolbarcontainer-dockcornermode-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarFloatingOptions-cornerMode?: DockCornerMode--><!--Device-ToolBarFloatingOptions-cornerMode?: DockCornerMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dockAreas

```TypeScript
dockAreas?: DockArea[]
```

浮动工具栏允许停靠的区域。默认值：全部8个区域。

**Type:** [DockArea](arkts-arkui-arkui-advanced-toolbarcontainer-dockarea-e.md)[]

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarFloatingOptions-dockAreas?: DockArea[]--><!--Device-ToolBarFloatingOptions-dockAreas?: DockArea[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## draggable

```TypeScript
draggable?: boolean
```

浮动工具栏是否可拖拽。默认值：true。true表示支持拖拽，false表示禁止拖拽。

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarFloatingOptions-draggable?: boolean--><!--Device-ToolBarFloatingOptions-draggable?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minimizeConfigs

```TypeScript
minimizeConfigs?: ToolBarMinimizeConfigs
```

浮动工具栏悬浮球的最小化配置。

**Type:** [ToolBarMinimizeConfigs](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarminimizeconfigs-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarFloatingOptions-minimizeConfigs?: ToolBarMinimizeConfigs--><!--Device-ToolBarFloatingOptions-minimizeConfigs?: ToolBarMinimizeConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
