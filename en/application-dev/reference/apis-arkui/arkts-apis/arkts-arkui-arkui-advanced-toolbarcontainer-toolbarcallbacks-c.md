# ToolBarCallbacks

```TypeScript
export class ToolBarCallbacks
```

用于工具栏拖拽、吸附以及状态回调的合集。

**Since:** 26.1.0

<!--Device-unnamed-export class ToolBarCallbacks--><!--Device-unnamed-export class ToolBarCallbacks-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarState, DockArea, DockCornerMode, ToolBarSafeAreaMode, HandednessAdaptationMode, ToolBarFloatingOptions, ToolBarFloatingConfigs, ToolBarMinimizeOptions, ToolBarMinimizeConfigs, ToolBarController, ToolBarInitialParams, ToolBarParams, ToolBarConfigs, ToolBarCallbacks, ToolBarDockOffsetOptions, ToolBarSafeAreaOptions, ToolBarContainerOptions, ToolBarContainerConfigs, ToolBarContainer, ToolBarDragStateCallback, ToolBarDragOffsetCallback, ToolBarStateCallback, ToolBarDockCallback, } from '@kit.ArkUI';
```

## onDock

```TypeScript
onDock?: ToolBarDockCallback
```

工具栏停靠到新区域时的回调。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarCallbacks-onDock?: ToolBarDockCallback--><!--Device-ToolBarCallbacks-onDock?: ToolBarDockCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDrag

```TypeScript
onDrag?: ToolBarDragOffsetCallback
```

拖拽过程中的回调，返回X/Y轴偏移量，单位为vp。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarCallbacks-onDrag?: ToolBarDragOffsetCallback--><!--Device-ToolBarCallbacks-onDrag?: ToolBarDragOffsetCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDragEnd

```TypeScript
onDragEnd?: ToolBarDragStateCallback
```

用户结束拖拽时的回调。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarCallbacks-onDragEnd?: ToolBarDragStateCallback--><!--Device-ToolBarCallbacks-onDragEnd?: ToolBarDragStateCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDragStart

```TypeScript
onDragStart?: ToolBarDragStateCallback
```

用户开始拖拽工具栏时的回调。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarCallbacks-onDragStart?: ToolBarDragStateCallback--><!--Device-ToolBarCallbacks-onDragStart?: ToolBarDragStateCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onStateChange

```TypeScript
onStateChange?: ToolBarStateCallback
```

工具栏状态变化时的回调。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarCallbacks-onStateChange?: ToolBarStateCallback--><!--Device-ToolBarCallbacks-onStateChange?: ToolBarStateCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
